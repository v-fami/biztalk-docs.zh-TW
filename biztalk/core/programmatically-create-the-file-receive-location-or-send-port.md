---
title: 以程式設計方式建立檔案接收位置或傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 558a414c-60bc-4f62-9397-a023ed4937fb
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 424c2c61655da599c4f437d3fdbf200df29d4e13
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013711"
---
# <a name="programmatically-create-the-file-receive-location-or-send-port"></a>以程式設計方式建立檔案接收位置或傳送埠
如何建立檔案接收埠，以及以程式設計方式傳送埠。 若要使用[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，請前往[設定 File 配接器](../core/configure-the-file-adapter.md)。

FILE 配接器將其組態資訊儲存在 SSO 資料庫中。 您可以設定接收位置和傳送埠以程式設計方式使用 「 BizTalk 總管物件模型。 
 
## <a name="create-the-receive-location"></a>建立接收位置

「 BizTalk 總管物件模型會公開**IReceiveLocation**組態介面，其中包含**TransportTypeData**讀/寫屬性。 此屬性接受 FILE 接收位置組態屬性包，其形式為名稱/值組 XML 字串。  
  
**TransportTypeData**屬性**IReceiveLocation**介面沒有設定。 若未設定，會使用 FILE 接收位置組態的預設值。  
  
 下表列出您可用程式設計方式為 FILE 接收位置設定的組態屬性。  
  
|屬性名稱|類型|描述|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|**FileNetFailRetryCount**|長整數|當網路共用上的接收位置暫時無法使用時，嘗試存取該接收位置的次數。|Integer<br /><br /> 最小值：0<br /><br /> 最大值： MAX_LONG|若未指定，會將預設值設定為 5 次。|  
|**FileNetFailRetryInterval**|長整數|當網路共用上的接收位置暫時無法使用時，嘗試存取該接收位置的重試間隔 (以分為單位)。|Integer<br /><br /> Minimumvalue: 0<br /><br /> 最大值： MAX_LONG|若未指定，會將預設值設定為 5 分鐘。|  
|**BatchSize**|長整數|此接收位置一次可以提交給伺服器的檔案數目。|Integer<br /><br /> 最小值： 1<br /><br /> 最大值： 256|若未指定，會將預設值設定為 20 個檔案。|  
|**FileMask**|String|接收位置使用的檔案遮罩。|String<br /><br /> FilePath 與 FileMask 結合的長度不能超過 256 個字元。|若未指定，會將預設值設定為 *.xml。|  
|**檔案路徑**|String|接收位置所監控的資料夾路徑。|String<br /><br /> 必要項<br /><br /> FilePath 與 FileMask 結合的長度不能超過 256 個字元。|必須指定**重要事項：** 建立接收位置必須有接收位置上設定的接收處理常式認證的 「 寫入 」 權限的檔案資料夾。|  
|**使用者名稱**|String|用來存取資料夾的帳戶使用者名稱。|最小長度： 0<br /><br /> 最大長度： 256|若未指定使用者名稱或密碼，會使用主控件認證。<br /><br /> 若為空值 (vt=”1”)，則會使用儲存在組態資料庫中的值。|  
|**密碼**|String|用來存取資料夾的帳戶密碼。|最小長度： 0<br /><br /> 最大長度： 256|若未指定使用者名稱或密碼，會使用主控件認證。<br /><br /> 若為空值 (vt=”1”)，則會使用儲存在組態資料庫中的值。|  
  
 下列程式碼顯示您用來設定屬性的 XML 字串格式：  
  
```  
<CustomProps>  
   <FilePath vt="8">C:\Temp</FilePath>  
   <BatchSize vt="19">20</BatchSize>  
   <FileMask vt="8">*.xml</FileMask>  
   <FileNetFailRetryCount vt="19">5</FileNetFailRetryCount>  
   <FileNetFailRetryInterval vt="19">5</FileNetFailRetryInterval>  
   <Username vt=”8”>MyDomain\MyUsername</Username>  
   <Password vt=”8”>PASSWORD</Password>  
</CustomProps>  
  
```  

## <a name="create-the-send-port"></a>建立傳送埠

組態資訊會儲存在自訂 XML 屬性包中。 `bts_file_properties.xsd`檔案傳送處理常式屬性結構描述定義檔案配接器特有的屬性。 您使用這些屬性來設定 FILE 傳送埠，以及在伺服器內傳遞配接器特定資訊。  
  
「 BizTalk 總管物件模型會公開**ITransportInfo**配接器組態介面 File 傳送埠，其中包含**TransportTypeData**讀/寫屬性。 此屬性接受 FILE 傳送處理常式組態屬性包做為名稱/值組 XML 字串。  
  
 設定**TransportTypeData**屬性**ITransportInfo**介面並非必要。 若不設定該屬性，會使用 FILE 傳送處理常式組態的預設值。  
  
 您可在 FILE 傳送處理常式位置的 BizTalk 總管物件模型中，以程式設計的方式設定下表列出的組態屬性。  
  
|屬性名稱|類型|描述|  
|-------------------|----------|-----------------|  
|**CopyMode**|長整數|定義將訊息寫入檔案時使用的複製模式。 有效值為：<br /><br /> **附加 (0)。** 若檔案存在，FILE 傳送處理常式會開啟檔案，並將訊息附加到檔案結尾。 若檔案不存在，FILE 傳送處理常式會建立新檔案。<br /><br /> **建立新的 (1)。** 若檔案不存在，FILE 傳送處理常式會建立新檔案並寫入檔案。 若檔案已存在，FILE 傳送處理常式會報告錯誤，然後依照傳送埠的一般配接器重試邏輯來處理。 此為 FILE 傳送處理常式的預設複製模式。<br /><br /> **覆寫 (2)。** 若檔案存在，FILE 傳送處理常式會開啟檔案，並覆寫其內容。 若檔案不存在，FILE 傳送處理常式會建立新檔案。|  
|**AllowCacheOnWrite**|布林|定義將訊息寫入檔案時，FILE 配接器是否使用檔案系統快取。<br /><br /> 有效值為：<br /><br /> **True (-1)** File 配接器會使用檔案系統快取寫入輸出檔時。<br /><br /> **False (0)** File 傳送處理常式不會使用檔案系統快取寫入輸出檔時。|  
|**寫入時使用暫存檔案**|布林|定義是否先將輸出檔寫入暫存檔，然後等寫入作業完成後再重新命名檔案。 如果啟用此選項，則會建立暫存檔案，副檔名為**BTS-WIP**。<br /><br /> 有效值為：<br /><br /> **True (-1)** File 配接器會寫入目標資料夾時，會建立暫存檔案。<br /><br /> **False (0)** File 配接器不會寫入目標資料夾時建立暫存檔案。 **注意：** 此選項時，才可用**CopyMode**屬性設定為值**建立新的 (1)**。|  
  
 若訊息內容中的任何組態屬性都沒有值，則 FILE 傳送處理常式會使用本身的預設值。  
  
 您可以使用程式設計的方式，在訊息內文上設定組態屬性。 您可以在協調流程或自訂管線元件中設定這些屬性。 使用這些屬性時適用下列規則：  
  
- 若組態屬性是在協調流程或接收管線中的自訂管線元件中設定，則：  
  
  -   若訊息傳送至靜態傳送埠，屬性值會以該傳送埠設定的值覆寫。  
  
  -   若訊息傳送至動態傳送埠，則不會覆寫屬性值。  
  
- 若組態屬性是在傳送管線的自訂管線元件中設定，則：  
  
  -   無論訊息是傳送至靜態或動態傳送埠，都不會覆寫值。  
  
  下列程式碼顯示可用來設定屬性的 XML 字串格式：  
  
```  
<CustomProps>  
   <CopyMode vt="19">0</CopyMode>  
   <AllowCacheOnWrite vt="11">-1</AllowCacheOnWrite>  
   <UseTempFileOnWrite vt="11">-1</UseTempFileOnWrite>  
</CustomProps>  
```  


