---
title: InfoPath 安全性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, InfoPath forms
- InfoPath forms, security
ms.assetid: 6ed7b5cc-9801-45a5-8fdb-e5d56dd36435
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ec5478af7c404840bf1c5c80be5520e405bd26a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209654"
---
# <a name="infopath-security"></a>InfoPath 安全性
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007年會使用 XML 簽章可讓您數位簽章使用數位憑證表單。 XML 簽章定義了一種標準 xml 數位簽章您用來協助保護在 XML 文件中所包含的資料。 XML 簽章是由全球資訊網協會 (W3C) 標準。  
  
 數位簽章是驗證的巨集或文件上電子、 加密型安全性戳記。 當數位簽章[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單中，透過表單輸入的 XML 執行個體 「 貼上戳記 」 的數位簽章 (簽章公用金鑰和帶正負號的資料摘要會寫入至 XML 中的專用節點)。 此簽章確認 XML 文件的簽名和未被改變。 [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]提供驗證、 非否定交易簽署、 部分簽署、 cosigning 和副署透過支援增強的數位簽章。  
  
 SWIFT [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] A4SWIFT 所提供的 FormGenerator 公用程式產生的表單，讓簽章來彼此交互堆疊 countersigners 使用數位簽章的 countersigning 方法。 這個 countersigning 簽章堆疊模型建立或編輯 SWIFT 訊息、 檢閱及核准一或多個檢閱者和核准者，根據訊息以及最後提交訊息的工作流程中的所有階段後才人力導向程的序已。  
  
 Repairers]、 [檢閱者] 或 [核准者簽署不論它們是否核准或拒絕訊息。 簽章表示回應的真實性，並不一定表示 「 已接受 」 的決策。  
  
 當[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]提交表單時，它會檢查訊息的有效性，簽章格式的使用者位於正確的角色。  
  
 如果在任何階段 （除了修復） 工作流程中將會拒絕訊息，訊息會傳送回修復階段。 如果訊息遭拒絕在 repairer 或建立者階段，訊息修復和新送出將訊息傳送回 Message Repair 和 New Submission 協調流程執行個體具有特定屬性將訊息標示為 拒絕。  
  
 本章節描述如何 Message Repair 和 New Submission 處理為角色定義的功能為基礎的數位簽章。 工作流程中的角色和功能的組合稱為 「 階段 」。  
  
> [!NOTE]
>  「 建立 」 角色是限制為單一的建立者跨部門。  
  
 此部分包含：  
  
-   [建立並修復階段](../../adapters-and-accelerators/accelerator-swift/creating-and-repairing-stages.md)  
  
-   [重設金鑰驗證階段](../../adapters-and-accelerators/accelerator-swift/rekey-verification-stage.md)  
  
-   [核准階段](../../adapters-and-accelerators/accelerator-swift/approval-stage.md)  
  
-   [散發的數位簽章](../../adapters-and-accelerators/accelerator-swift/distributing-digital-certificates.md)