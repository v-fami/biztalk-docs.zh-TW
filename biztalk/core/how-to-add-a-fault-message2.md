---
title: 如何新增錯誤個訊息 2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- fault messages, adding
- messages, fault messages
ms.assetid: 8f1b40af-2c75-4167-8b62-a86b791907c9
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6dee8a1fca0e30a96b6a714b5c717c0638bc8144
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246454"
---
# <a name="how-to-add-a-fault-message"></a>如何新增錯誤訊息
當 您建立連接後端系統的連接埠時，會包含要求和回應 。 您必須新增訊息，以便將該訊息指派給錯誤。  
  
### <a name="to-add-a-fault-message"></a>若要新增錯誤訊息  
  
1.  在**協調流程檢視**視窗中，以滑鼠右鍵按一下**訊息**，然後選取**新訊息**。  
  
     Message_3 隨即建立，您可將它專門指派給該錯誤。  
  
2.  以滑鼠右鍵按一下 Message_3，然後選取**屬性**。  
  
3.  在**屬性** 對話方塊中，將**訊息類型**。  
  
     選取 **.NET 類別**，然後選取  **systemstring**。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling3.md)