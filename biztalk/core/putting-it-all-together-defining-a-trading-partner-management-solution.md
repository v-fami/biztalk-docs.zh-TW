---
title: "整合在一起： 定義交易夥伴管理解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4219312a-c4b5-45f3-b77b-d5cc4f1a1ca4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea32fba8e9e57d7a0549a680b06e08d5bf8e087f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="putting-it-all-together-defining-a-trading-partner-management-solution"></a>整合在一起： 定義交易夥伴管理解決方案
在瞭解用來建立 TPM 方案的不同元件類型後，接著要介紹典型的 TPM 方案流程，以及如何合併使用不同的建置組塊。 本節也列示建立 TPM 方案模型的一些最佳做法。  
  
 建立 TPM 方案的典型流程包含以下各項：  
  
1.  建立代表商務交易中之所有相關組織的夥伴。 例如，如果有兩個商業組織和商務交易有關，必須為每個組織建立一個交易夥伴。 如需有關如何建立交易夥伴的指示，請參閱[設定一般合作對象屬性](../core/configuring-general-party-properties.md)或[設定一般合作對象屬性 (AS2)](../core/configuring-general-party-properties-as2.md)  
  
2.  對於組織內的每個業務部門，在夥伴中建立代表業務部門的設定檔。 例如，如果組織包含「採購」和「供應」業務部門，必須在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中各以一個商務設定檔分別代表每個部門。 另外，除了為代表您組織的夥伴建立商務設定檔之外，也必須為與您交易的夥伴建立商務設定檔。 如需有關如何建立商務設定檔的指示，請參閱[設定商務設定檔屬性](../core/configuring-business-profile-properties.md)。  
  
3.  為每個商務設定檔定義 B2B 通訊協定設定 (含訊息編碼設定與訊息通訊協定設定)。 這些設定定義 B2B 訊息如何編碼，以及如何在兩個商務設定檔之間傳輸。  
  
    > [!NOTE]
    >  在此階段中，指定通訊協定設定是可省略的。 您可以直接在交易夥伴協議中新增通訊協定設定。  
  
4.  建立商務設定檔之間的交易夥伴協議 (TPA)，此協議定義兩個商務設定檔交換訊息時同意使用的編碼和/或訊息通訊協定。 如需有關如何建立協議的指示，請參閱[設定 X12 特有協議屬性](../core/configuring-x12-specific-agreement-properties.md)，[設定 EDIFACT 特定協議屬性](../core/configuring-edifact-specific-agreement-properties.md)，或[設定 AS2協議屬性](../core/configuring-as2-agreement-properties.md)。  
  
 執行上述工作集合，您會建立與交易夥伴交換 B2B 訊息的 TPM 方案。  
  
## <a name="where-do-i-start"></a>要從何處著手？  
 您可透過下列各節開始進行：  
  
-   X12 特定教學課程[教學課程 2: EDI 介面開發人員教學課程](../core/tutorial-2-edi-interface-developer-tutorial.md)。  
  
-   AS2 特定教學課程[教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md)。  
  
-   X12-和 EDIFACT-底下的特定逐步解說[開發和設定 BizTalk Server EDI 方案](../core/developing-and-configuring-biztalk-server-edi-solutions.md)。  
  
-   底下的 AS2 特定逐步解說[開發和設定 BizTalk Server AS2 解決方案](../core/developing-and-configuring-biztalk-server-as2-solutions.md)。  
  
-   建立合作對象、 設定檔和協議的 X12 和 EDIFACT 傳訊依照指示在[設定 EDI 屬性](../core/configuring-edi-properties.md)。  
  
-   建立合作對象、 設定檔，並依照指示在訊息的 AS2 合約[設定 AS2 屬性](../core/configuring-as2-properties.md)。  
  
## <a name="see-also"></a>另請參閱  
 [交易夥伴管理方案的建置組塊](../core/building-blocks-of-a-trading-partner-management-solution.md)