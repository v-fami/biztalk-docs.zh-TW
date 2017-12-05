---
title: "移除傳送埠 （BizTalk Server 範例） |Microsoft 文件"
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
- send ports, deleting
- deleting, send ports
ms.assetid: e6643525-fa9f-4d39-880f-314749a68471
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8b82af2be42342d51429e42d1952816ee0dd07a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="remove-send-port-biztalk-server-sample"></a>移除傳送埠 （BizTalk Server 範例）
「移除傳送埠」範例會示範如何取消登錄一或多個傳送埠，並且將其移除。  
  
> [!WARNING]
>  如果在部署後不需要部署指令碼，就應該將其移除。 必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 構成本範例之指令檔中的 Visual Basic Scripting Edition (VBScript) 指令碼，會示範如何使用 BizTalk Server WMI 提供者來執行下列作業：  
  
-   在指定傳送埠名稱情況下，查詢相符傳送埠的清單。  
  
    > [!NOTE]
    >  一般而言，只有一個傳送埠會符合指定的名稱。  
  
-   取消登錄這些傳送埠。  
  
-   刪除這些傳送埠。  
  
-   處理任何錯誤，讓有意義的資訊能傳回給使用者。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 這個範例位於下列 SDK 位置：  
  
 \<*範例路徑*\>\Admin\WMI\Remove 傳送 Port\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|在 \VBScript 資料夾中：<br /><br /> RemoveSendPort.vbs|VBScript 檔案，它會接收一個參數，而該參數會指定一或多個要取消登錄和移除的傳送埠。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 「移除傳送埠」範例是由單一的 VBScript 檔案組成，而您並不需要建置或初始化該檔案。  
  
## <a name="running-this-sample"></a>執行此範例  
  
#### <a name="to-run-the-remove-send-port-sample"></a>若要執行移除傳送埠範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*\>\Admin\WMI\Remove 接收 Port\VBScript\  
  
2.  執行 RemoveSendPort.vbs 檔案，它會使用 cscript 程式，並傳遞下列命令列引數：  
  
     **\<** ***SendPortName* \>。** 要移除之傳送埠的名稱。 如果傳送埠名稱包含空格，請用引號括住該名稱。  
  
     例如：  
  
    ```  
    cscript RemoveSendPort.vbs "My Business Send Port"  
    ```  
  
## <a name="comments"></a>註解  
 您也可以使用會存取 Windows WMI 物件模型的指令碼，執行所有可在 BizTalk Server 管理主控台中執行的工作。  
  
 指令檔 RemoveSendPort.vbs 包含詳細註解，其中含有其所執行作業的深入說明。 如需詳細資訊，請參閱 < 在 Windows Management Instrumentation [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102)。  
  
## <a name="see-also"></a>請參閱  
 [Admin-WMI (BizTalk Server Samples 資料夾)](../core/admin-wmi-biztalk-server-samples-folder.md)