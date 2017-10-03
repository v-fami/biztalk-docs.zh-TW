---
title: "中樞架構實例的範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- supply chains, examples
- hub-and-spoke systems
- supply chains, hub-and-spoke systems
- examples, supply chains
- trading partners, supply chains
ms.assetid: ee92c24d-a281-4950-a61e-9cb3bd08d291
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b417398786e602379d16d6734a5ed366b9d6f2ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sample-hub-based-scenario"></a>範例中樞架構實例
在許多供應鏈實例中，公司將與每個交易夥伴合作設立 RosettaNet 實作架構 (RNIF) 連線。 這是標準化整個供應鏈通訊的有效方式。 此案例中所述[範例提供鏈結案例](../../adapters-and-accelerators/accelerator-rosettanet/sample-supply-chain-scenario.md)。  
  
 另一個自動化整個供應鏈交易的方式，是公司與其他公司簽約，設定及管理整合系統。 這是使用中樞架構的實例。  
  
## <a name="how-a-hub-based-system-works"></a>中樞架構系統的運作方式  
 在中樞架構系統中，簽約使用整合系統的公司會透過 RNIF 連線連接至中樞公司。 接著中樞公司會使用所需的任何電子連線類型，連接到公司的所有交易夥伴。 中樞公司提供所有交易夥伴的連線選項：RNIF 連線、EDI、一般檔案、Web 應用程式或非相容的專屬連線。 管理通訊系統是中樞公司的責任。 下圖顯示這類系統如何運作。  
  
 ![&#60;沒有變更 &#62;] (../../adapters-and-accelerators/accelerator-rosettanet/media/hub-based-scenario.gif "Hub_Based_Scenario")  
  
 中樞架構系統具有許多優點：  
  
-   簽約公司不用處理供應鏈的複雜性；中樞公司將負責處理這些工作。  
  
-   簽約公司不用維護或升級系統，也不負責處理當機；系統維護與當機維修都由中樞公司負責。  
  
-   簽約公司可以獲得 RosettaNet 相容系統的好處，包括標準化、自動化、節省成本以及透明度。  
  
-   簽約公司可以透過各種電子連線自動化本身的供應鏈，這些連線讓交易夥伴擁有完備的連線選擇。 簽約公司也不用具備維護各種連線選擇的技術性專業知識。  
  
-   只要中樞公司支援，交易夥伴就可以繼續使用專屬連線。  
  
-   系統具有彈性。 交易夥伴不必採用 RosettaNet 相容系統。 不過，交易夥伴若採用 RosettaNet 相容系統，將會從這種系統大大受益。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何解決商務需求](../../adapters-and-accelerators/accelerator-rosettanet/how-biztalk-server-solves-the-business-need1.md)   
 [交易夥伴整合需求](../../adapters-and-accelerators/accelerator-rosettanet/the-need-for-trading-partner-integration.md)   
 [供應鏈面臨的挑戰](../../adapters-and-accelerators/accelerator-rosettanet/the-supply-chain-challenge.md)   
 [供應鏈方案](../../adapters-and-accelerators/accelerator-rosettanet/the-supply-chain-solution.md)   
 [範例供應鏈實例](../../adapters-and-accelerators/accelerator-rosettanet/sample-supply-chain-scenario.md)