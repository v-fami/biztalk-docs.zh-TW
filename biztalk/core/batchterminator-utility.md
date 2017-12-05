---
title: "BatchTerminator 公用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 771241fa-7df5-4882-8430-c2f36200cc9d
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 080f82993fc3c8c62b3764d496f03589bd06364e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="batchterminator-utility"></a>BatchTerminator 公用程式
BatchTerminator 公用程式可讓您終止所有用來批次處理 EDI 交換的即時批次處理協調流程。 當您擁有大量正在執行的批次處理協調流程執行個體，而您需要終止所有的批次才可以針對 BizTalk 伺服器系統執行維護作業時，這個公用程式保證可發揮其功用。  
  
 BatchTerminator 公用程式位於[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities\MicrosoftEDI\BatchTerminator 資料夾。 當您執行公用程式來終止批次處理協調流程執行個體時，此公用程式會將結果記錄在 batchterminator.log 檔案\<*磁碟機*\>: \Documents and 設定\\<*使用者名*\>\Application Data 資料夾。  
  
> [!NOTE]
>  BatchTerminator 公用程式才支援在 32 位元系統上。  BatchTerminator Microsoft.BizTalk.ExplorerOM 命名空間，才能支援從 32 位元處理序中使用元件。  
  
 **重新啟動終止的協調流程執行個體**  
  
 當您終止一群協調流程執行個體之後，您就可以針對這些執行個體進行大量重新啟動。 您可以使用 /Activate 參數，以及可指示已遭停止批次之檔案的名稱和路徑，進行這項重新啟動。 當您執行此公用程式來終止一群協調流程執行個體時，公用程式會建立這個已遭停止批次的檔案。 停止批次檔是 batchSettings-\<GUID\>中的.xml \<*磁碟機*\>: \Documents and 設定\\<*使用者名稱* \>\Application data 資料夾。 已遭停止批次之檔案的路徑和名稱，也會儲存在該 log 檔案內。 當此公用程式配合 /activate 參數執行時，它會就某個結構描述來驗證輸入檔案。  
  
 **語法**  
  
 在命令列視窗中，以下列語法來執行 BatchTerminator 公用程式：  
  
```  
BatchTerminator /<switch>  
```  
  
 您可以配合下列參數來執行 BatchTerminator 公用程式。 若未提供任何參數，則將使用 /terminate 選項。 正如以下所示，您可以輸入像是 /terminate 的完整參數名稱，或是縮短形式，以此例來說就是 /t。  
  
|||  
|-|-|  
|參數|函數|  
|/?|顯示說明|  
|/ 結束的記錄檔：\<*記錄檔*\><br /><br /> 或 /t-記錄檔：\<*記錄檔*\>|將終止控制訊息傳送給所有作用中的 X12 或 EDIFACT 批次處理協調流程執行個體。 這個動作會顯示作業的結果，包括它所終止之所有作用中批次協調流程執行個體的清單，它所找到的作用中批次協調流程數目，以及它已傳送的終止控制訊息的數目。 它將結果記錄到 batchterminator.log 檔案\<*磁碟機*\>: \Documents and 設定\\<*使用者名*\>\應用程式儲存資料夾。<br /><br /> 選用的-記錄： 參數可讓您指定記錄檔的名稱和/或您想要儲存到記錄檔資料夾的路徑。 使用指定的路徑和檔案名稱參數的範例如下所示： `BatchTerminator.exe /terminate -log:"C:\logs\log.txt"`。 使用參數來指定檔案名稱的範例只會如下所示： `BatchTerminator.exe /terminate -log:log.txt`。 如果指定的路徑無效，此公用程式會使用預設路徑： \<*磁碟機*\>: \Documents and 設定\\<*使用者名*\>\Application 資料。 -Log： 參數可以用，不論 /terminate 參數。|  
|/print<br /><br /> 或 /p|顯示一份不傳送終止控制訊息之目前作用中批次處理協調流程執行個體的清單|  
|啟動 /:\<*路徑*\>\\<br />batchSettings-\<*GUID*\>.xml-記錄檔：\<*記錄檔*\><br /><br /> 或 /a:\<*路徑*\>\\<br />batchSettings-\<*GUID*\>.xml-記錄檔：\<*記錄檔*\>|重新啟動先前已終止的協調流程執行個體所述的 batchSettings-\<GUID\>.xml 檔案。 公用程式會就程式碼內嵌的結構描述，驗證該輸入檔案。 如果該輸入檔案與該結構描述不相符，這時螢幕上就會印出錯誤訊息，而該程式將會結束。<br /><br /> 若有包括 -log: 參數，這個作業就會將關於重新啟動動作的資訊寫入至記錄檔。|  
  
 **批次啟動檔案的格式**  
  
 若要重新啟用之前終止批次協調流程執行個體使用 / 啟動參數，您必須提供批次啟動檔案 (batchSettings-\<GUID\>.xml)。 這個檔案必須採用下列格式：  
  
```  
<?xml version="1.0"?>  
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" elementFormDefault="qualified" id="BatchInfo" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="BatchTerminator">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element minOccurs="1" maxOccurs="unbounded" name="Batch">  
          <xs:complexType>  
            <xs:attribute name="PartyName" type="xs:string" />  
            <xs:attribute name="PartyID" type="xs:int" use="required" />  
            <xs:attribute name=”BatchName” type=”xs:string” />  
            <xs:attribute name=”BatchID” type=”xs:int” use=”required” />  
            <xs:attribute name="EdiMessageType" type="xs:string" use="required" />  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="prerequisites"></a>必要條件  
 下列是執行本主題所述程序的必要條件：  
  
-   您必須以「BizTalk Server 系統管理員」群組的成員身分登入。  
  
### <a name="to-run-the-batchterminator-utility"></a>若要執行 BatchTerminator 公用程式  
  
1.  在 Windows 檔案總管 中，移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities\MicrosoftEDI\BatchTerminator 資料夾。  
  
2.  Enter **BatchTerminator**，包括任何需要的參數，然後按一下**Enter**。  
  
3.  在 Windows 檔案總管 中，移至\<*磁碟機*\>: \Documents and 設定\\<*使用者名*\>\Application Data 資料夾，並開啟 batchterminator.log 檔案，以查看結果的記錄。  
  
## <a name="see-also"></a>請參閱  
 [SDK 中的公用程式](../core/utilities-in-the-sdk.md)