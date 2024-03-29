---
title: 如何終止擱置的協調流程執行個體 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, terminating [HAT]
- messages, saving [HAT]
- HAT, saving messages
- HAT, terminating pipelines
- HAT, terminiating orchestrations
- orchestrations, terminating [HAT]
ms.assetid: b5d44cce-b05c-47f9-9015-5b10c2312bf1
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37de5e1153e9d361b76900ca206351e8b9549dc3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991967"
---
# <a name="how-to-terminate-suspended-orchestration-instances"></a>如何終止擱置的協調流程執行個體
您可以從 BizTalk Server 管理主控台中的 [查詢結果] 或 [預覽] 窗格，終止任何擱置的協調流程執行個體或連接埠。  
  
> [!NOTE]
>  排序傳遞傳送埠的每一個執行個體都可能會有關聯的數個訊息。 為了防止意外終止或資料流失，請務必檢閱所有的這類關聯之後，再終止執行個體。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「BizTalk Server 操作員」群組的成員身分登入，才能執行此程序。  
  
### <a name="to-terminate-suspended-orchestration-instances"></a>終止擱置的協調流程執行個體  
  
1. 按一下 **開始**，按一下**程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中展開 [[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]]，然後按一下 BizTalk 群組。  
  
3. 在 詳細資料 窗格中，按一下**新的查詢** 索引標籤。  
  
4. 在 **查詢運算式**群組中**值**欄中，選取**已擱置服務執行個體**從下拉式清單方塊。  
  
5. 執行下列其中之一：  
  
   - 若要終止單一執行個體，**欄位名**星號旁邊的空白下拉式清單方塊中的資料行 (**\\**<em>)，選取 **服務名稱</em>* 篩選器，然後在**值** 欄中，指定服務名稱。  
  
   - 若要終止大量執行個體，**欄位名**星號旁邊的空白下拉式清單方塊中的資料行 (**\\**<em>)，選取 **群組結果依據</em>* ，然後在**值** 欄中，指定服務名稱。  
  
6. 按一下 **執行查詢**。  
  
7. 在查詢結果清單中，以滑鼠右鍵按一下您想要終止，然後按一下 執行個體群組的協調流程執行個體**終止執行個體**或是**終止執行個體**。  
  
## <a name="see-also"></a>另請參閱  
 [調查協調流程、連接埠和訊息失敗](../core/investigating-orchestration-port-and-message-failures.md)