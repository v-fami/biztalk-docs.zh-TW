---
title: "啟動傳送埠 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, examples
- examples, send ports
- send ports, starting
ms.assetid: 84e54c9e-e9e8-4bb2-a191-20c29e127dae
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f293d00848c32f6b519349543c8a39824d9bca8c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="start-send-port-biztalk-server-sample"></a>啟動傳送埠 （BizTalk Server 範例）
「啟動傳送埠」範例示範如何在使用 FILE 配接器時啟動傳送埠並選擇性地設定主要傳輸位址。  
  
> [!WARNING]
>  如果在部署後不需要部署指令碼，就應該將其移除。 必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 構成本範例之指令檔中的 Visual Basic Scripting Edition (VBScript) 指令碼，會示範如何使用 BizTalk Server WMI 提供者來執行下列作業：  
  
-   在指定傳送埠名稱情況下，查詢相符傳送埠的清單。  
  
    > [!NOTE]
    >  一般而言，只有一個傳送埠會符合指定的名稱。  
  
-   設定這些傳送埠的主要傳輸位址 (相對於安裝路徑)。  
  
-   啟動這些傳送埠。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 這些範例檔案位於下列 SDK 位置：  
  
 \<*範例路徑*\>\Admin\WMI\Start 傳送 Port\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|在 \VBScript 資料夾中：<br /><br /> StartSendPort.vbs|VBScript 檔案，其使用參數指定要啟動的傳送埠，並選擇性地指定與該傳送埠相關聯之主要傳輸位址的新值。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 「啟動傳送埠」範例是由單一的 VBScript 檔案組成，而您並不需要建置或初始化該檔案。  
  
## <a name="running-this-sample"></a>執行此範例  
  
#### <a name="to-run-this-sample"></a>執行此範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*\>\Admin\WMI\Start 傳送 Port\VBScript\  
  
2.  使用 cscript 程式執行 StartSendPort.vbs 檔案，以便傳遞下列命令列引數，其中第二個引數是選用項目：  
  
    -   **\<** ***SendPortName* \>。** 要啟動之傳送埠的名稱。 如果傳送埠名稱包含空格，請用引號括住該名稱。  
  
    -   **\<** ***PrimaryTransportAddress* \>。** 主要傳輸位址 (相對於產品安裝位置)，藉由指定此參數可加以變更。 如果主要配接器位址包含空格，請用引號括住此位址。  
  
         例如：  
  
        ```  
        cscript StartSendPort.vbs "My Business Send Port" SDK\Samples\HelloWorld\Out\%MessageID%.xml  
        ```  
  
## <a name="comments"></a>註解  
 您也可以使用會存取 Windows WMI 物件模型的指令碼，執行所有可在 BizTalk Server 管理主控台中執行的工作。  
  
 指令檔 StartSendPort.vbs 包含詳細註解，其中含有其所執行作業的深入說明。 如需詳細資訊，請參閱 < 在 Windows Management Instrumentation [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102)。  
  
## <a name="see-also"></a>請參閱  
 [Admin-WMI (BizTalk Server Samples 資料夾)](../core/admin-wmi-biztalk-server-samples-folder.md)