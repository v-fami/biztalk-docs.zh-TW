---
title: 如何新增範圍 Shape4 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adding, Scope shapes
- Scope shape, adding
ms.assetid: 4ed56ada-a656-40b1-b34a-0c0803c01216
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a81bb85412784616d185b64ee39f1e777d19fea3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248326"
---
# <a name="how-to-add-a-scope-shape"></a>如何新增範圍圖形
請遵循下列步驟來新增**範圍**圖形。  
  
### <a name="to-add-a-scope-shape"></a>若要新增範圍圖形  
  
1.  以滑鼠右鍵按一下下方的箭號**receivefromin**通訊埠，請指向**插入圖形**，然後按一下 **範圍**。  
  
     在 [範圍] 圖形中，設定可能有錯誤的作業。  
  
     例如，在 SQLExecute 協調流程中加入傳送作業、接收作業和傳送埠。 在這個範例中，您會傳送訊息至 SERVER。 SERVER 會提供回應。 然後執行其餘的協調流程，並將資訊傳回給 OutFile 連接埠。  
  
2.  在 「 範圍 」 圖形，設定**交易**至**無**。  
  
3.  「 範圍 」 圖形內按一下滑鼠右鍵，然後選取**新例外狀況處理常式**。  
  
     這會建立**Catch 例外狀況**區塊。 從後端發生的例外狀況，它會攔截到內部**Catch 例外狀況**區塊。  
  
4.  在**Catch 例外狀況**區塊中，您必須加入的邏輯。  
    在必須設定的邏輯中，最重要的一個就是您預期會收到的錯誤訊息類型。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling4.md)