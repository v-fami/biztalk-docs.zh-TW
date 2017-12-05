---
title: "停止協調流程 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
- orchestrations, stopping
ms.assetid: 83be44e9-819d-4ac5-8b75-84c23e6b5ba2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b0c88bdeb85b8ad493b85d2569061c35bd516e1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="stop-orchestration-biztalk-server-sample"></a>停止協調流程 （BizTalk Server 範例）
「停止協調流程」範例會示範如何停止 BizTalk Server 協調流程，以及選擇性地將它取消登錄。  
  
> [!WARNING]
>  如果在部署後不需要部署指令碼，就應該將其移除。 必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 構成本範例之指令檔中的 Visual Basic Scripting Edition (VBScript) 指令碼，會示範如何使用 BizTalk Server WMI 提供者來執行下列作業：  
  
-   在指定協調流程名稱和組件名稱的情形下，查詢已部署的特定 BizTalk Server 協調流程。  
  
-   停止該協調流程。  
  
-   取消登錄該協調流程 (選擇性)。  
  
-   處理任何錯誤，讓有意義的資訊能傳回給使用者。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 這些範例檔案位於下列 SDK 位置：  
  
 \<*範例路徑*\>\Admin\WMI\Stop Orchestration\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|在 \VBScript 資料夾中：<br /><br /> StopOrch.vbs|會使用參數的 VBScript 檔案，這些參數會指定要停止和 (選擇性) 取消登錄的協調流程。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 「停止協調流程」範例是由單一 VBScript 檔案組成，您並不需要建置或初始化該檔案。  
  
## <a name="running-this-sample"></a>執行此範例  
  
#### <a name="to-run-this-sample"></a>執行此範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*\>\Admin\WMI\Stop Orchestration\VBScript\  
  
2.  執行 StopOrch.vbs 檔案，它會使用 cscript 程式，並傳遞下列命令列引數，其中第三個引數是選擇性引數：  
  
    -   **\<** ***OrchestrationName* \>。** 要停止及 (選擇性) 要取消登錄之 BizTalk Server 協調流程的名稱。  
  
    -   **\<** ***AssemblyName* \>。** 其中已部署指定之協調流程的 BizTalk 組件名稱。 如果組件名稱包含空格，請用引號括住該名稱。  
  
    -   **取消登錄。** 選用的常值字串，表示除了停止指定之協調流程以外，還要將其取消登錄。  
  
         例如：  
  
        ```  
        cscript StopOrch.vbs MyBusinessOrchestration "My Business Assembly"  
        ```  
  
         -或-  
  
        ```  
        cscript StopOrch.vbs MyBusinessOrchestration MyBusinessAssembly Unenlist  
        ```  
  
## <a name="comments"></a>註解  
 您也可以使用會存取 Windows WMI 物件模型的指令碼，執行所有可在「BizTalk Server 管理主控台」中執行的工作。  
  
 指令檔 StopOrch.vbs 包含詳細註解，其中含有其所執行作業的深入說明。 如需詳細資訊，請參閱 < 在 Windows Management Instrumentation [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102)。  
  
## <a name="see-also"></a>請參閱  
 [Admin-WMI (BizTalk Server Samples 資料夾)](../core/admin-wmi-biztalk-server-samples-folder.md)