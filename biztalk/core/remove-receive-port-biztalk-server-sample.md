---
title: "移除接收埠 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive ports, examples
- deleting, receive ports
- examples, receive ports
- receive ports, deleting
ms.assetid: de97d914-b8e8-4365-8041-3b455c351f86
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d15442da8afd4829245b742bdd45af8f7d1f832
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="remove-receive-port-biztalk-server-sample"></a>移除接收埠 （BizTalk Server 範例）
「移除接收埠」範例會示範如何移除一或多個接收埠。  
  
> [!WARNING]
>  如果在部署後不需要部署指令碼，就應該將其移除。 必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 構成本範例之指令檔中的 Visual Basic Scripting Edition (VBScript) 指令碼，會示範如何使用 BizTalk Server WMI 提供者來執行下列作業：  
  
-   指定接收埠名稱，查詢相符的接收埠的清單。  
  
    > [!NOTE]
    >  一般而言，只有一個接收埠會符合指定的名稱。  
  
-   移除這些接收埠。  
  
-   處理任何錯誤，讓有意義的資訊能傳回給使用者。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 這些範例位於下列 SDK 位置：  
  
 \<*範例路徑*\>\Admin\WMI\Remove 接收 Port\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|在 \VBScript 資料夾中：<br /><br /> RemoveReceivePort.vbs|VBScript 檔案，它會接收特定參數來指定一或多個要移除的接收埠。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 「移除接收埠」範例是由單一的 VBScript 檔案組成，而您並不需要建置或初始化該檔案。  
  
## <a name="running-this-sample"></a>執行此範例  
  
#### <a name="to-run-this-sample"></a>執行此範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*\>\Admin\WMI\Remove 接收 Port\VBScript\  
  
2.  使用 cscript 程式執行 RemoveReceivePort.vbs 檔案，並傳遞下列命令列引數：  
  
     **\<** ***ReceivePortName* \>** 。 要移除之接收埠的名稱。 如果接收埠名稱包含空格，請用引號括住該名稱。  
  
     例如：  
  
    ```  
    cscript RemoveReceivePort.vbs "My Business Receive Port"  
    ```  
  
## <a name="comments"></a>註解  
 您也可以使用會存取 Windows WMI 物件模型的指令碼，執行所有可在 BizTalk Server 管理主控台中執行的工作。  
  
 指令檔 RemoveReceivePort.vbs 包含詳細註解，內容會更進一步地解釋此檔案所執行作業的相關資訊。 如需詳細資訊，請參閱 < 在 Windows Management Instrumentation [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102)。  
  
## <a name="see-also"></a>請參閱  
 [Admin-WMI (BizTalk Server Samples 資料夾)](../core/admin-wmi-biztalk-server-samples-folder.md)