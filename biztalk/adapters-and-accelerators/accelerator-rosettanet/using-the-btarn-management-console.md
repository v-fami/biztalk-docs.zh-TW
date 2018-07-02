---
title: 使用 BTARN 管理主控台 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- agreements, activating
- activating agreements
- BTARN Management Console, Scope pane
- tracking
- creating, trading partners
- BTARN Management Console, agreements
- process configuration
- agreements, modifying
- BTARN Management Console, home organizations
- agreements, creating
- BTARN Management Console, trading partners
- agreements, deleting
- deleting, agreements
- BTARN Management Console
- agreements, listing
- modifying, trading partners
- creating, agreements
- trading partners, creating
- modifying, agreements
- BAM tracking
- Scope pane [BTARN Management Console]
- trading partners, modifying
- trading partners, deleting
- BTARN Management Console, process configurations
- deleting, trading partners
- BTARN Management Console, about BTARN Management Console
- home organizations
ms.assetid: 000ee93d-eb1d-4ff8-a9cf-0547beff027d
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b35c054e78f09edbe84d799b7218d4921b83795c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977919"
---
# <a name="using-the-btarn-management-console"></a>使用 BTARN 管理主控台
本主題描述如何從 [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 管理主控台管理 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]。  
  
 開啟[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]管理主控台中，按一下**開始**、 指向**程式**，指向**Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]**Management Console**。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台的範圍 (左側) 窗格包含所有 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 組態節點。 結果 (右側) 窗格包含在範圍窗格中所選組態項目的全部特定執行個體。  
  
## <a name="operations-in-the-scope-pane"></a>在範圍窗格中可以進行的作業  
 您可以在範圍窗格中的節點，執行下列作業：  
  
- 設定供交易夥伴傳送埠使用的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 傳送與接收管線。 如需詳細資訊，請參閱 <<c0> [ 設定 BTARN 傳送管線和接收管線](../../adapters-and-accelerators/accelerator-rosettanet/setting-btarn-send-and-receive-pipelines.md)。  
  
- 啟用「商務活動監控」(BAM) 追蹤。 如需詳細資訊，請參閱 <<c0> [ 啟用 BAM 追蹤](../../adapters-and-accelerators/accelerator-rosettanet/enabling-bam-tracking.md)。  
  
- 請確定任何新匯入的組態是在主控台中顯示，以滑鼠右鍵按一下 [範圍] 窗格中的 [設定] 節點，然後按一下**重新整理**。  
  
- 檢視結果] 窗格中的其他資料行，以滑鼠右鍵按一下**程序組態設定**或是**協議**節點在範圍窗格中，指向**檢視**，然後按一下 [**新增/移除欄位**。 使用可用的資料行和顯示的資料行之間移動資料行**新增或移除** 按鈕。 當協議具有許多可用的欄位，但 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 預設不顯示這些欄位時，這個命令就會特別有用處。  
  
## <a name="process-configurations"></a>程序組態  
 您可以針對程序組態，執行下列作業：  
  
-   加入新的程序組態，以滑鼠右鍵按一下**程序組態設定**範圍節點，指向**新增**，然後按一下**程序組態**。 如需詳細資訊，請參閱 <<c0> [ 如何建立或編輯流程組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。  
  
-   編輯現有的程序組態，以滑鼠右鍵按一下處理程序組態，在 [結果] 窗格中，然後按一下**屬性**，或按兩下程序組態。 如需詳細資訊，請參閱 <<c0> [ 如何建立或編輯流程組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。  
  
-   刪除現有的程序組態，以滑鼠右鍵按一下處理程序組態，在 [結果] 窗格中，然後按一下**刪除**。  
  
-   建立新的程序組態，根據現有的程序組態，以滑鼠右鍵按一下您想要根據新的組態，[結果] 窗格中的組態，然後按一下**新的程序組態，從複本**. 這會顯示新**程序組態屬性**對話方塊填入現有組態的設定。 輸入新**顯示程式碼**，然後按一下**確定**來建立新的組態。 如需詳細資訊，請參閱 <<c0> [ 使用 PIP 規格建立程序組態](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md)。  
  
-   顯示一份程序組態以滑鼠右鍵按一下 [結果] 窗格中的特定組態，然後按一下相關聯的所有協議**顯示協議**。 這會將焦點移至**協議**在範圍窗格中的節點，並在 [結果] 窗格中顯示關聯的協議。 您可以還原為協議的完整清單，以滑鼠右鍵按一下**協議**範圍窗格中，然後按一下 節點**全部顯示**。  
  
## <a name="home-organizations"></a>主要組織  
 您可以針對主要組織，執行下列作業：  
  
-   加入新的主要組織，以滑鼠右鍵按一下**所在地組織**範圍節點，指向**新增**，然後按一下**主要組織**。 如需詳細資訊，請參閱 <<c0> [ 建立或編輯主要組織](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md)。  
  
-   以滑鼠右鍵按一下 主要組織，在 結果 窗格中，然後按一下 編輯現有的主要組織**屬性**，或按兩下主要組織。 如需詳細資訊，請參閱 <<c0> [ 建立或編輯主要組織](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md)。  
  
-   以滑鼠右鍵按一下 主要組織，在 結果 窗格中，然後按一下 刪除現有的主要組織**刪除**。  
  
## <a name="partners"></a>合作夥伴  
 您可以針對交易夥伴，執行下列作業：  
  
-   新增夥伴，以滑鼠右鍵按一下**合作夥伴**範圍節點，指向**新增**，然後按一下**夥伴**。 如需詳細資訊，請參閱 <<c0> [ 建立或編輯夥伴](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)。  
  
-   以滑鼠右鍵按一下 [結果] 窗格中的夥伴，然後按一下來編輯現有的協力廠商**屬性**，或按兩下交易夥伴。 如需詳細資訊，請參閱 <<c0> [ 建立或編輯夥伴](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)。  
  
-   [結果] 窗格中，在夥伴上按一下滑鼠右鍵，然後按一下要刪除現有的交易夥伴**刪除**。  
  
## <a name="agreements"></a>協議  
 您可以針對協議，執行下列作業：  
  
-   以滑鼠右鍵按一下新增新合約**協議**範圍節點，指向**新增**，然後按一下**協議**。 如需詳細資訊，請參閱 <<c0> [ 建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)。  
  
-   以滑鼠右鍵按一下 [結果] 窗格中的協議，然後按一下來編輯現有的協議**屬性**，或按兩下協議。 如需詳細資訊，請參閱 <<c0> [ 建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)。  
  
-   以滑鼠右鍵按一下 協議，在 結果 窗格中，然後按一下 刪除現有的協議**刪除**。  
  
-   以滑鼠右鍵按一下 已停用協議，在 結果 窗格中，然後按一下 啟動協議**Activate**。 如此會啟用與要收送的協議相關的訊息。 您也可以停用協議以避免傳送或接收任何與協議關聯的訊息。  
  
-   還原之後顯示清單的程序組態相關聯，協議的協議的完整清單上按一下滑鼠右鍵**協議**範圍窗格中，然後按一下 節點**全部顯示**.  
  
## <a name="see-also"></a>另請參閱  
 [設定 BTARN 傳送和接收管線](../../adapters-and-accelerators/accelerator-rosettanet/setting-btarn-send-and-receive-pipelines.md)   
 [啟用 BAM 追蹤](../../adapters-and-accelerators/accelerator-rosettanet/enabling-bam-tracking.md)   
 [如何建立或編輯流程組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)   
 [建立或編輯主要組織](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md)   
 [建立或編輯夥伴](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)   
 [建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)