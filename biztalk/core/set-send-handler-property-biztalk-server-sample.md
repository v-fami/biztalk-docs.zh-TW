---
title: "設定 Send Handler 屬性 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SMTP adapters, examples
- examples, SMTP adapters
- send handlers, properties
ms.assetid: eb6ae2f2-528f-44ec-bca4-f37006893ff2
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0e14f58cbdd07a8c13dec6cd44fbc95584f2ecc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="set-send-handler-property-biztalk-server-sample"></a>設定 Send Handler 屬性 （BizTalk Server 範例）
設定 Send Handler 屬性範例會示範如何設定 Simple Mail Transfer Protocol (SMTP) 傳送處理常式的 XML 組態資訊。  
  
> [!WARNING]
>  如果在部署後不需要部署指令碼，就應該將其移除。 必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 構成本範例之指令檔中的 Visual Basic Scripting Edition (VBScript) 指令碼，會示範如何使用 BizTalk Server WMI 提供者來執行下列作業：  
  
-   在指定傳送處理常式名稱情況下，查詢相符傳送處理常式的清單。  
  
-   設定 SMTP 傳送處理常式的 XML 組態資訊。  
  
-   處理任何錯誤，讓有意義的資訊能傳回給使用者。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 這些範例檔案位於下列 SDK 位置：  
  
 \<*範例路徑*> \Admin\WMI\Set 傳送處理常式 Property\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|在 \VBScript 資料夾中：<br /><br /> ConfigureSMTP.vbs|VBScript 檔案，它會接受多個參數，而這些參數會指定 SMTP 傳送處理常式和「寄件者」電子郵件地址。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 「設定 Send Handler 屬性」範例是由單一的 VBScript 檔案組成，而您並不需要建置或初始化該檔案。  
  
## <a name="running-this-sample"></a>執行此範例  
  
#### <a name="to-run-the-set-send-handler-property-sample"></a>若要執行設定 Send Handler 屬性範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*> \Admin\WMI\Set 傳送處理常式 Property\VBScript\  
  
2.  執行 ConfigureSMTP.vbs 檔案，它會使用 cscript 程式，並傳遞下列命令列引數：  
  
    -   **\<**   
         ***SMTPServerName* >。** 將會用來傳送郵件之 SMTP 伺服器的名稱。  
  
    -   **\<**   
         ***FromEmailAddress* >。** 將會用來做為「寄件者」地址的電子郵件地址。  
  
         例如：  
  
        ```  
        cscript ConfigureSMTP.vbs MyBusinessSMTPServer someone@example.com  
        ```  
  
## <a name="comments"></a>註解  
 您也可以使用會存取 Windows WMI 物件模型的指令碼，執行所有可在 BizTalk Server 管理主控台中執行的工作。  
  
 指令檔 ConfigureSMTP.vbs 包含詳細註解，其中含有其所執行作業的深入說明。 如需詳細資訊，請參閱 < 在 Windows Management Instrumentation [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102)。  
  
## <a name="see-also"></a>另請參閱  
 [管理 WMI （BizTalk Server 範例資料夾）](../core/admin-wmi-biztalk-server-samples-folder.md)