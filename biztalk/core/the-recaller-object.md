---
title: "Recaller 物件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Recaller object
- Invoke method
- process management solution tutorial, Recaller object
- process management solution tutorial, errors
ms.assetid: b30ad1ae-475f-4913-b402-4d3263fcf072
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 731f7703eb9145b1249872902d0b867fe22622ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-recaller-object"></a>Recaller 物件
商務程序管理解決方案會以一般的方法來重試某些失敗的物件方法呼叫。 這個解決方案會執行透過**Recaller**物件存放至**ExceptionHandler**協調流程。 **ExceptionHandler**協調流程會使用重試物件方法呼叫的物件。 如需詳細資訊，請參閱[ExceptionHandler 協調流程](../core/the-exceptionhandler-orchestration.md)。  
  
## <a name="the-invoke-method"></a>Invoke 方法  
 **Recaller**物件有一個單一的靜態方法， **Invoke**。 因為它是靜態的您永遠不需要建立的執行個體**Recaller**物件。 您可以使用**Invoke**方法，以三種方式： 來建構物件，請呼叫靜態方法或呼叫物件的非靜態方法的物件。  
  
> [!NOTE]
>  **Invoke**方法做為包裝函式**Type.InvokeMember**方法中的[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]類別庫。  
  
### <a name="arguments-for-the-invoke-method"></a>Invoke 方法的引數  
 下表描述的引數**Invoke**方法：  
  
|參數|類型|Description|  
|---------------|----------|-----------------|  
|*t*|**型別**|呼叫方法的物件類型。|  
|*obj*|**物件**|要使用的物件執行個體。|  
|*方法名稱*|**string**|要叫用的方法名稱。|  
|*引數*|**陣列**|類型的陣列**物件**包含方法的引數。|  
  
 若要呼叫物件建構函式，請使用空字串 ("") 或**null**如*methodName*。  
  
 若要呼叫靜態方法，使用**null**如*obj*。  
  
 若要呼叫非靜態方法，請提供所有引數。  
  
> [!NOTE]
>  使用**null**做為型別引數的值*t*，會導致**Invoke**擲回**ArgumentNullException**例外狀況。 引數*t*不應為 null 因為**Invoke**方法會使用**Type.InvokeMember** [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]方法。  
  
## <a name="calling-invoke"></a>呼叫 Invoke  
 在方案中，只有**ExceptionHandler**協調流程使用**Recaller**物件。 **ExceptionHandler** ，接著，正由其他協調流程。 若要傳送的值， **Invoke**方法是從這些其他協調流程。 例如，下列程式碼會出現在**Activate**中的協調流程**InitialException**運算式 」 圖形：  
  
```  
Ex = CodeEx;  
ObjectType = orderHandler.GetType();  
CalledObject = orderHandler;  
Reason = "Standard Activate Failed";  
MethodName = "Activate";  
ParameterArray = System.Array.CreateInstance(typeof(System.Object),  
                                              3 );  
ParameterArray.SetValue(ServiceType, 0);  
ParameterArray.SetValue(OrderMsg.CustNum, 1);  
ParameterArray.SetValue(OrderMsg.OrderNum, 2);  
ReturnValue = null; // no return value expected  
  
```  
  
 請注意程式碼建立陣列使用**System.Array.CreateInstance**並用**SetValue**方法，可儲存在它所使用的值。  
  
 在運算式圖形之後呼叫 Activate 協調流程**ExceptionHandler**協調流程。 下列程式碼顯示協調流程設計師如何轉譯「呼叫」圖形：  
  
```  
call Microsoft.Samples.  
    BizTalk.SouthridgeVideo.  
        OrderManager.ExceptionHandlerOrch  
            (  
                Reason,  
                Ex,  
                CalledObject,  
                MethodName,   
                ParameterArray,   
                OrderCorrelation,   
                OrderMsg,   
                out ReturnValue,   
                ObjectType  
            );  
  
```  
  
 在**ExceptionHandler**協調流程中，下列程式碼會出現在**Call Original Code**運算式 」 圖形：  
  
```  
ReturnValue =   
    Microsoft.Samples.  
        BizTalk.SouthridgeVideo.  
            Utilities.Recaller.  
                Invoke(  
                    ObjectType,  
                    CalledObject,  
                    MethodName,  
                    ParameterArray  
                );  
```  
  
 請注意，雖然引數名稱符合 Activate 協調流程呼叫中的引數名稱，但呼叫協調流程時，是依照順序而不是名稱來對應引數。  
  
## <a name="see-also"></a>另請參閱  
 [商務程序管理解決方案的實作重點](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [ExceptionHandler 協調流程](../core/the-exceptionhandler-orchestration.md)