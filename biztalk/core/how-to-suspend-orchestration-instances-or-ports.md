---
title: 如何擱置協調流程執行個體或連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10f6923df37b5cce3a500ed6e02014f09d1c2c0f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994927"
---
# <a name="how-to-suspend-orchestration-instances-or-ports"></a>如何擱置協調流程執行個體或連接埠
您可以從 BizTalk Server 管理主控台的查詢結果清單中擱置協調流程執行個體或連接埠。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「BizTalk Server 操作員」群組的成員身分登入，才能執行此程序。  
  
### <a name="to-suspend-orchestration-instances-or-ports"></a>擱置協調流程執行個體或連接埠  
  
1. 按一下 **開始**，按一下**程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，然後按一下 BizTalk 群組。  
  
3. 在 詳細資料 窗格中，按一下**新的查詢** 索引標籤。  
  
4. 在 **查詢運算式**群組中**值**欄中，選取**執行的服務執行個體**從下拉式清單方塊。  
  
5. 執行下列其中之一：  
  
   - 若要暫停的單一執行個體，**欄位名**星號旁邊的空白下拉式清單方塊中的資料行 (**\\**<em>)，選取 **服務名稱</em>* 篩選器，然後在**值** 欄中，指定服務名稱。  
  
   - 若要暫停其大量執行個體，**欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (**\\**<em>)，選取 **群組結果依據</em>* ，然後在**值** 欄中，指定服務名稱。  
  
6. 按一下 **執行查詢**。  
  
7. 在查詢結果清單中，以滑鼠右鍵按一下您想要暫停，然後按一下 作用中的協調流程或連接埠**暫止的執行個體**或是**擱置執行個體**。  
  
## <a name="see-also"></a>另請參閱  
 [調查協調流程、連接埠和訊息失敗](../core/investigating-orchestration-port-and-message-failures.md)