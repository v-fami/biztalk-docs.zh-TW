---
title: "如何擱置協調流程執行個體或連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, suspending
- instances, suspending
- suspending
- HAT, suspending orchestrations
- HAT, suspending pipelines
- suspending, ports
- suspending, orchestrations
- orchestrations, suspending
- HAT, suspending ports
- suspending, instances
- ports, suspending
ms.assetid: cacc7e58-7d3e-4d6b-adb0-618fdc4f0d89
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62d91c8d1e02b7283a430f7c82c572b6a989d108
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-suspend-orchestration-instances-or-ports"></a>如何擱置協調流程執行個體或連接埠
您可以從 BizTalk Server 管理主控台的查詢結果清單中擱置協調流程執行個體或連接埠。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「BizTalk Server 操作員」群組的成員身分登入，才能執行此程序。  
  
### <a name="to-suspend-orchestration-instances-or-ports"></a>擱置協調流程執行個體或連接埠  
  
1.  按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，然後按一下 BizTalk 群組。  
  
3.  在 詳細資料 窗格中，按一下**新查詢** 索引標籤。  
  
4.  在**查詢運算式**群組中**值**欄中，選取**執行服務執行個體**從下拉式清單方塊。  
  
5.  執行下列其中之一：  
  
    -   若要在暫停的單一執行個體，**欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (**\***)，請選取**服務名稱**篩選和接著在**值**資料行中，指定服務名稱。  
  
    -   若要擱置大量執行個體，在**欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (**\***)，請選取**群組結果依據**，然後在**值**資料行中，指定服務名稱。  
  
6.  按一下**執行查詢**。  
  
7.  在查詢結果清單中，以滑鼠右鍵按一下您想要暫停，然後按一下 作用中協調流程或連接埠**暫停的執行個體**或**擱置執行個體**。  
  
## <a name="see-also"></a>另請參閱  
 [調查協調流程、 連接埠和訊息失敗](../core/investigating-orchestration-port-and-message-failures.md)