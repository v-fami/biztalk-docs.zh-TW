---
title: 執行 Orchestrations2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- strong name keys, creating
- orchestrations
- creating strong name keys
- compiling orchestrations
- host instances, stopping and restarting
- deployment, orchestrations
- orchestrations, compiling
- orchestrations, deploying
- stopping host instances
- restarting host instances
ms.assetid: a098d552-d302-44f6-9af9-d77d16549fd3
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c299486c8ca43b34ba93ce434245b52b30e567aa
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981047"
---
# <a name="running-orchestrations"></a>執行協調流程
下列程序說明如何建置、部署、繫結和啟動協調流程。  
  
## <a name="creating-a-strong-name-key"></a>建立強式名稱金鑰  
  
#### <a name="to-create-a-strong-name-key"></a>若要建立強式名稱金鑰  
  
1. 開啟 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 命令提示字元。  
  
2. 將目錄變更為現有的專案，然後按 ENTER 鍵。  
  
    例如：  
  
    **\<drive\>:\Adapter_Install\biztalk\my_project**  
  
3. 在命令提示字元中輸入下列文字，然後按 ENTER：  
  
    `sn -k SSOSchedule.snk`  
  
## <a name="compiling-and-deploying-an-orchestration"></a>編譯和部署協調流程  
  
#### <a name="to-compile-and-deploy-an-orchestration"></a>若要編譯和部署協調流程  
  
1. 在 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案總管] 中，以滑鼠右鍵按一下**SSOSchedule**專案，然後選取**屬性**。  
  
2. 按一下 **通用屬性**，展開**組件**節點。  
  
3. 輸入的路徑中輸入 ssoschedule.snk**組件金鑰檔案**文字方塊。  
  
4. 確認 Configuration Properties\Deployment\Server 是一個點 （.） 或您的電腦名稱，然後按一下**確定**。  
  
5. 在 [方案總管] 中，以滑鼠右鍵按一下**SSOSchedule**，然後按一下**重建**。  
  
6. 以滑鼠右鍵按一下**SSOSchedule**，然後按一下**部署**。  
  
## <a name="starting-the-orchestration"></a>啟動協調流程  
  
#### <a name="to-start-the-orchestration"></a>若要啟動協調流程  
  
1. 按一下 **開始**，指向**所有程式**，指向**Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理]。**  
  
2. 在 BizTalk Server 管理主控台中，展開**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，依序展開 所需應用程式，，然後按一下**協調流程**。  
  
3. 在 詳細資料 窗格中，以滑鼠右鍵按一下協調流程，然後按一下 **啟動**。  
  
## <a name="stopping-and-restarting-a-host-instance"></a>停止並重新啟動主控件執行個體  
 部署範例之後，您必須重新啟動主控件執行個體。  
  
#### <a name="to-stop-and-restart-a-host-instance"></a>若要停止並重新啟動主控件執行個體  
  
1. 按一下 **開始**，指向**所有程式**，指向**Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理]。**  
  
2. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理]**，展開**BizTalk 群組**，依序展開**平台設定**，然後按一下 [ **主控件執行個體**。  
  
3. 在右窗格中，請以滑鼠右鍵按一下主控件執行個體 （例如，電腦名稱），然後按一下 **停止**。  
  
    主控件執行個體狀態會變更為**已停止**。  
  
4. 在右窗格中，以滑鼠右鍵按一下主控件執行個體，然後按一下 **啟動**。  
  
    主控件執行個體狀態會變更為**開始擱置**。  
  
    若要將狀態變更為**執行**然後按一下**重新整理**，或以滑鼠右鍵按一下主控件執行個體，然後按一下**重新整理**。  
  
## <a name="see-also"></a>另請參閱  
 [保護配接器](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)