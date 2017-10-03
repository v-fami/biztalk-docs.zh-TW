---
title: "如何使用 呼叫規則圖形 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Rules shape [Orchestration Designer], how to
- Call Rules shape [Orchestration Designer], configuring
- Call Rules shape [Orchestration Designer], policies
- policies, Call Rules shape [Orchestration Designer]
ms.assetid: e4bc8a2c-de7e-4e3a-81b8-12bcebb17d27
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a634c2e0a97e627925390610bf4c3039c8afc85c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-call-rules-shape"></a>如何使用呼叫規則圖形
在協調流程設計師中，您可以使用**呼叫規則**圖形以呼叫商務原則。  
  
### <a name="to-configure-the-call-rules-shape"></a>設定呼叫規則圖形  
  
1.  從 工具箱 中**BizTalk 協調流程**索引標籤，拖曳**呼叫規則** 圖形至協調流程設計介面上的連接線上。  
  
     -或者-  
  
     以滑鼠右鍵按一下的連接線或圖形預留位置您要加入圖形，指向 **插入圖形**操作功能表，然後按一下**呼叫規則**。  
  
    > [!NOTE]
    >  在[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]，您不需要有要插入的不可部分完成範圍**呼叫規則**圖形。 您可以拖曳**呼叫規則**從工具箱拖曳圖形到協調流程設計介面。 不過，在[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]、**呼叫規則**功能表項目已停用操作功能表中如果您嘗試插入**呼叫規則**圖形的協調流程沒有不可部分完成的範圍內。 這是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 產品的限制。  
  
2.  在協調流程設計師中，選取**呼叫規則**圖形。  
  
3.  按兩下圖形以顯示**[CallRules 原則組態**] 對話方塊。  
  
4.  在**選取您想要呼叫的商務原則**下拉式清單中，選取您需要的原則。  
  
    > [!NOTE]
    >  呼叫規則組態在決定原則要使用的類型時，將查詢最新儲存的原則版本。 在執行階段，則將使用最新部署的原則版本。  
  
5.  在**指定原則參數**清單方塊中，選取 從變數**參數名稱**屬性。  
  
    > [!NOTE]
    >  **呼叫規則**圖形基本上會重新建構訊息，如同使用**建構**圖形，這可能造成遺失訊息內容屬性。  
  
    > [!NOTE]
    >  您可以指定訊息或.NET 變數做為 BRE 原則的參數。 要傳遞**TypedXmlDocument**事實中，指定對應的訊息在協調流程中做為參數宣告。 若要通過.NET 事實，指定做為參數的協調流程中宣告的.NET 變數。 若要將資料庫事實，指定型別的.NET 變數**DataConnection**或**TypedDataTable**做為參數的原則。