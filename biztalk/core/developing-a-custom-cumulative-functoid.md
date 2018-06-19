---
title: 開發自訂累計運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ea2c5fa-ed50-4b76-aee9-0d4adf9e6d8c
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f69ae870269948358f117b07f37d481faced160
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22242326"
---
# <a name="developing-a-custom-cumulative-functoid"></a>開發自訂累計運算質
使用自訂累計運算質以執行在執行個體訊息中發生多次之值的累積運算。  
  
 在開發累計運算質時，您必須實作三個函式。 此三個函式對應至對應執行累積所需的初始化、累計和取得動作。 在討論這些函式之前，必須先討論執行緒安全。  
  
## <a name="writing-a-thread-safe-functoid"></a>撰寫安全執行緒運算質  
 運算質程式碼必須為安全執行緒，因為在承受壓力的狀況下，對應的多個執行個體可能會同時執行。 有些重點必須熟記：  
  
-   靜態狀態必須為安全執行緒。  
  
-   執行個體狀態並不一定要是安全執行緒。  
  
-   設計時請考量在高壓力狀況下執行。 儘可能避免鎖定。  
  
-   儘可能避免同步化需求。  
  
 BizTalk Server 提供一個簡單的機制，以降低撰寫安全執行緒累計運算質的複雜性。 這三個函式皆具有相同的第一個參數，該參數為整數索引值。 在呼叫初始化函式時，BizTalk Server 會指派唯一的編號給索引值。 您可以使用此值做為保存累積值之陣列中的索引，如下列程式碼所示：  
  
```  
private HashTable cumulativeArray = new HashTable();  
…  
// Initialization function  
public string InitCumulativeMultiply(int index)  
{  
    cumulativeArray[index] = 1.0;  
    return string.Empty;  
}  
```  
  
 此範例使用 HashTable 代替 ArrayList。 這是因為初始化函式可能不是以排序索引值呼叫。  
  
## <a name="implementing-the-three-cumulative-functions"></a>實作三個累計函式  
 您將需要為所開發的每個自訂累計運算質實作三個函式。 下表摘要說明您必須在建構函式中呼叫以設定的函式與方法。 所有函式均傳回字串值。  
  
> [!NOTE]
>  您可以為每個函式決定最適當的名稱，不過每個函式都必須具有指定引數的數目和類型。  
  
|函式目的|引數|設定參考|設定內嵌指令碼|  
|----------------------|---------------|------------------------|--------------------------|  
|初始化|**int 索引**|**SetExternalFunctionName**|**SetScriptBuffer**與`functionNumber`= 0|  
|累計|**int 索引、 字串 val、 字串範圍**|**SetExternalFunctionName2**|**SetScriptBuffer**與`functionNumber`= 1|  
|Get|**int 索引**|**SetExternalFunctionName3**|**SetScriptBuffer**與`functionNumber`= 2|  
  
### <a name="initialization"></a>初始化  
 初始化可讓您準備將用來執行累積的機制。 您可以初始化陣列、重設一或多個值，或視需要載入其他資源。 不會使用字串傳回值。  
  
### <a name="cumulation"></a>累計  
 您在此為運算質執行適當的累積運算。 BizTalk Server 會傳入下列三個參數：  
  
-   **索引。** 代表對應執行個體的整數值。 可能會有多個對應執行個體同時執行。  
  
-   **Val。** 包含應累積之值的字串。 除非您正在撰寫字串累計運算質，否則此值為數字值。  
  
-   **範圍。** 包含指示應累積哪些項目或屬性值之數字的字串。 實際的值由實作決定。  
  
 您可以決定要累積哪些值以及忽略哪些值。 例如，您可以忽略不是低於 0 的值，但是當某個值不是數字時，擲回例外狀況。 **BaseFunctoid**提供兩個函式 —**IsDate**和**IsNumeric**— 以協助驗證。  
  
> [!NOTE]
>  如果您使用**IsDate**或**IsNumeric**中內嵌指令碼，請務必設定**RequiredGlobalHelperFunctions**使函式會提供給您的指令碼。  
  
 不會使用字串傳回值。  
  
### <a name="get"></a>Get  
 當 BizTalk Server 完成重複處理由對應中的運算質設定所決定的所有值時，會要求累積值。 Get 函式具有一個 `Index` 引數，該引數為一個代表對應執行個體的整數值。 您的函式應使用索引值以尋找並傳回字串格式的累積值。  
  
## <a name="example"></a>範例  
 下列範例說明如何建立自訂運算質執行累計乘法。 它依賴包含三個字串資源以及一個 16x16 像素點陣圖資源的資源檔案。  
  
```  
using System;  
using Microsoft.BizTalk.BaseFunctoids;  
using System.Reflection;  
using System.Text;  
using System.Collections;  
using System.Globalization;  
  
namespace Microsoft.Samples.BizTalk.CustomFunctoid  
{  
    public class CumulativeMultiplyFunctoid : BaseFunctoid  
    {  
        private ArrayList myCumulativeArray = new ArrayList();  
  
        public CumulativeMultiplyFunctoid() : base()  
        {  
            //ID for this functoid  
            ID = 6001;  
  
            // Resource assembly must be ProjectName.ResourceName if building with VS.Net  
            SetupResourceAssembly("Microsoft.Samples.BizTalk.CustomFunctoid.CustomFunctoidResources", Assembly.GetExecutingAssembly());  
  
            // Pass the resource ID names for functoid name, tooltip  
            // description and the 16x16 bitmap for the Map palette  
            SetName("IDS_CUMULATIVEMULTIPLYFUNCTOID_NAME");  
            SetTooltip("IDS_CUMULATIVEMULTIPLYFUNCTOID_TOOLTIP");  
            SetDescription("IDS_CUMULATIVEMULTIPLYFUNCTOID_DESCRIPTION");  
            SetBitmap("IDB_CUMULATIVEMULTIPLYFUNCTOID_BITMAP");  
  
            // Put this string handling function under the Cumulative  
            // Functoid tab in the Visual Studio toolbox for functoids  
            Category = FunctoidCategory.Cumulative;  
  
            // 2 required parameters, no optional parameters  
            SetMinParams(1);  
            SetMaxParams(2);  
  
            // Functoid accepts three inputs  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
            AddInputConnectionType((~ConnectionType.FunctoidCount) & (~ConnectionType.FunctoidIndex) & (~ConnectionType.FunctoidIteration) & (~ConnectionType.FunctoidCumulative) & (~ConnectionType.FunctoidLooping) & (~ConnectionType.Record));  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
  
            // Set the output connection type  
            OutputConnectionType = ConnectionType.AllExceptRecord;  
  
            // Set the Initialize, Cumulative and Get functions  
            SetExternalFunctionName(GetType().Assembly.FullName, "Microsoft.Samples.BizTalk.CustomFunctoid.CumulativeMultiplyFunctoid", "InitCumulativeMultiply");  
            SetExternalFunctionName2("AddToCumulativeMultiply");  
            SetExternalFunctionName3("GetCumulativeMultiply");  
        }  
  
        // Initialization function  
        public string InitCumulativeMultiply(int index)  
        {  
            if (index >= 0)  
            {  
                if (index >= myCumulativeArray.Count)  
                {  
                    myCumulativeArray.Add(1.0);  
                }  
                else  
                {  
                    myCumulativeArray[index] = 1.0;  
                }  
            }  
  
            return "";  
        }  
  
        // Cumulative function  
        public string AddToCumulativeMultiply(int index, string val, string reserved)  
        {  
            if (index < 0 || index >= myCumulativeArray.Count)  
            {  
                return "";  
            }  
  
            if (IsNumeric(val))  
            {  
                double dval = Convert.ToDouble(val, CultureInfo.InvariantCulture);  
                myCumulativeArray[index] = (double)(myCumulativeArray[index]) * dval;  
            }  
            return myCumulativeArray[index].ToString();  
        }  
  
        // Get Function  
        public string GetCumulativeMultiply(int index)  
        {  
            if (index < 0 || index >= myCumulativeArray.Count)  
            {  
                return "";  
            }  
  
            return myCumulativeArray[index].ToString();  
        }  
    }  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用 BaseFunctoid](../core/using-basefunctoid.md)   
 [開發自訂內嵌運算質](../core/developing-a-custom-inline-functoid.md)   
 [自訂運算質 （BizTalk Server 範例）](../core/custom-functoid-biztalk-server-sample.md)