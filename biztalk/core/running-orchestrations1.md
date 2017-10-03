---
title: "執行 Orchestrations1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong name keys, creating
- orchestrations
- host instances, stopping and restarting
- orchestrations, compiling
- orchestrations, deploying
ms.assetid: b992bdba-630d-4f28-aca8-c568f3c27968
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3bc4326d5821dd9fb672d8dabf9751a3fa2d816
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-orchestrations"></a>執行協調流程
下列程序說明如何建置、部署、繫結和啟動協調流程。  
  
## <a name="creating-a-strong-name-key"></a>建立強式名稱金鑰  
  
#### <a name="to-create-a-strong-name-key"></a>若要建立強式名稱金鑰  
  
1.  啟動 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 命令提示字元。  
  
2.  例如，將目錄變更至現有的專案，\<磁碟機 >: \Adapter_Install\biztalk2010\my_project。  
  
3.  在命令提示字元中輸入下列文字，然後按 ENTER：  
  
     `sn -k SSOSchedule.snk`  
  
## <a name="compiling-and-deploying-an-orchestration"></a>編譯和部署協調流程  
  
#### <a name="to-compile-and-deploy-an-orchestration"></a>若要編譯和部署協調流程  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下 SSOSchedule 專案，然後選取**屬性**。  
  
2.  按一下**通用屬性**，然後展開**組件**節點。  
  
3.  輸入的路徑中輸入 ssoschedule.snk**組件金鑰檔案**文字方塊。  
  
4.  確認 Configuration properties\deployment\server 中包含點 （.） 或您的電腦名稱，然後按一下 **確定**。  
  
5.  在 [方案總管] 中，以滑鼠右鍵按一下**SSOSchedule**，然後按一下**重建**。  
  
6.  以滑鼠右鍵按一下**SSOSchedule**，然後按一下**部署**。  
  
## <a name="starting-the-orchestration"></a>啟動協調流程  
  
#### <a name="to-start-the-orchestration"></a>若要啟動協調流程  
  
1.  在 BizTalk 管理主控台中，選取您想要啟動協調的流程。  
  
2.  以滑鼠右鍵按一下協調流程，然後按一下**啟動**。  
  
## <a name="stopping-and-restarting-a-host-instance"></a>停止並重新啟動主控件執行個體  
 部署範例之後，您必須重新啟動主控件執行個體。  
  
#### <a name="to-stop-and-restart-a-host-instance"></a>若要停止並重新啟動主控件執行個體  
  
1.  按一下**啟動**，指向**所有程式**，指向 [ **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後選取**BizTalk Server 管理]。**  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按兩下**Microsoft BizTalk Server （本機）**  節點，然後展開**主機**。  
  
3.  在左窗格中，選取**BizTalkServerApplication**。  
  
4.  在右窗格中，以滑鼠右鍵按一下主控件執行個體 （例如，電腦名稱），然後按一下**停止**。  
  
     主控件執行個體狀態會變更為**已停止**。  
  
5.  在右窗格中，以滑鼠右鍵按一下主控件執行個體，然後按一下**啟動**。  
  
     主控件執行個體狀態會變更為**開始擱置**。  
  
     若要將狀態變更為**執行**，按一下 **重新整理**，或以滑鼠右鍵按一下主控件執行個體，然後按一下**重新整理**。  
  
## <a name="see-also"></a>另請參閱  
 [使用單一登入](../core/using-single-sign-on3.md)