---
title: "（適用於 Azure) 的步驟 3： 建立服務匯流排佇列 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7192c3c-4ebf-49c4-b8ce-46a6e9fb5f4a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d55b3222798edb245000cdde8de52565c39758a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-for-azure-create-a-service-bus-queue"></a>（適用於 Azure) 的步驟 3： 建立服務匯流排佇列
在本主題中，您可以建立服務匯流排佇列的 X12 銷售訂單傳送它的後面處理和轉換使用 EDI 協議。  
  
### <a name="to-create-a-service-bus-queue"></a>若要建立服務匯流排佇列  
  
1.  登入[Windows Azure CTP Management Portal](http://go.microsoft.com/fwlink/p/?LinkId=202886)使用您的 Microsoft 帳戶。  
  
2.  在較低的頁面左側，按一下  **AppFabric**。  
  
3.  在左側樹狀目錄中展開 服務、 展開您的訂閱，然後按一下命名空間中，您必須已經建立。 如果您還沒有命名空間，請參閱[How to： 建立或修改 Windows Azure CTP 服務命名空間](http://msdn.microsoft.com/library/windowsazure/hh697699.aspx)。  
  
4.  若要建立佇列按一下**新佇列**從**管理實體**從工具列則位於頁面頂端的類別。  
  
5.  在**新佇列**對話方塊方塊中，輸入佇列的名稱。 此教學課程中，輸入相同的名稱。 `queueordersedi`，然後按一下 **確定**。 您指定這個名稱做為您在建立 EDI 協議的一部分[(Azure) 的步驟 2： 建立 EDI 協議](../core/step-2-for-azure-create-an-edi-agreement.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)