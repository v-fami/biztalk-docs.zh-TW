---
title: "啟用接收位置 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, examples
- receive locations, enabling
- examples, receive locations
ms.assetid: dd04b38a-634d-4c9a-b31a-2f226fa91d19
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd2df85f051285e999660dc3765855d22c708939
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="enable-receive-location-biztalk-server-sample"></a>啟用接收位置 （BizTalk Server 範例）
「啟用接收位置」範例示範如何啟用接收位置，並選擇性地設定該接收位置的「輸入傳輸 URL」。  
  
> [!WARNING]
>  如果在部署後不需要部署指令碼，就應該將其移除。 必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 構成本範例之指令檔中的 Microsoft Visual Basic Scripting Edition (VBScript) 指令碼，會示範如何使用 BizTalk Server WMI 提供者來執行下列作業：  
  
-   在指定接收埠名稱和接收位置的情形下，查詢相符的接收位置清單。  
  
-   設定接收位置的輸入傳輸 URL (相對於安裝路徑)。  
  
-   啟用接收位置。  
  
-   處理任何錯誤，讓有意義的資訊能傳回給使用者。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 這個範例位於下列 SDK 位置：  
  
 \<*範例路徑*\>\Admin\WMI\Enable 接收 Location\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|在 \VBScript 資料夾中：<br /><br /> EnableRecLoc.vbs|VBScript 檔案，其會接收指定要啟用之接收位置的參數，以及選擇性地指定與該接收位置關聯之「輸入傳輸 URL」新值的參數。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 「啟用接收位置」範例是由單一 VBScript 檔案組成，您並不需要建置或初始化該檔案。  
  
## <a name="running-this-sample"></a>執行此範例  
  
#### <a name="to-run-this-sample"></a>執行此範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*\>\Admin\WMI\Enable 接收 Location\VBScript\  
  
2.  使用 cscript 程式執行 EnableRecLoc.vbs 檔案，並傳遞下列命令列引數，其中第三個引數是選擇性引數：  
  
    -   **\<** ***ReceivePortName* \>。** 包含要啟用之接收位置的接收埠名稱。 如果接收埠名稱包含空格，請用引號括住該名稱。  
  
    -   **\<** ***ReceiveLocationName* \>。** 要在指定之接收埠內啟用之接收位置的名稱。 如果接收位置名稱包含空格，請用引號括住該名稱。  
  
    -   **\<** ***InboundTransportURI* \>。** 接收配接器 URI (相對於產品安裝位置)，您可以指定此引數來變更該 URI。 如果輸入配接器 URI 包含空格，請用引號括住該 URI。  
  
         例如：  
  
        ```  
        cscript EnableRecLoc.vbs "My Business Receive Port" MyBusinessReceiveLocation  
        ```  
  
         -或-  
  
        ```  
        cscript EnableRecLoc.vbs MyBusinessReceivePort "My Business Receive Location" SDK\Samples\HelloWorld\In\*.xml  
        ```  
  
## <a name="comments"></a>註解  
 您也可以使用會存取 Windows WMI 物件模型的指令碼，執行所有可在 BizTalk Server 管理主控台中執行的工作。  
  
 指令檔 EnableRecLoc.vbs 包含詳細註解，內容會更進一步地解釋此檔案所執行作業的相關資訊。  
  
 如需詳細資訊，請參閱 < 在 Windows Management Instrumentation [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102)。  
  
## <a name="see-also"></a>請參閱  
 [Admin-WMI (BizTalk Server Samples 資料夾)](../core/admin-wmi-biztalk-server-samples-folder.md)