---
title: 交易夥伴使用 BizTalk Server 的管理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f31a5e49-ef19-41a3-9cf3-cf85d0685a59
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed1a3591314634c41cfd598aa074e497dd19ec03
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983719"
---
# <a name="trading-partner-management-using-biztalk-server"></a>使用 BizTalk Server 管理交易夥伴
## <a name="introduction-to-tpm"></a>TPM 的簡介
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 交易夥伴管理 (TPM) 對於如何管理與儲存夥伴和其業務的相關資訊，有著全新的基礎概念。 增強的 TPM 方案會反映實際商場上的商務實體與關係，讓組織更容易管理與交易夥伴之間的業務合作關係。 如需有關 TPM 方案如何塑造 BizTalk 環境中的之交易合作關係的詳細資訊，請參閱 <<c0> [ 交易夥伴管理解決方案的建置組塊](../core/building-blocks-of-a-trading-partner-management-solution.md)。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含電子資料交換 (EDI) 資料交換與 AS2 資料傳輸的原生支援。 這項支援讓企業能夠擴充以 EDI 為基礎的商務程序管理解決方案，並且充分利用自動化交換 EDI 交易所提供的產能改進優勢。 BizTalk Server 為企業提供使用 EDI 和 EDIINT/AS2 的方式，可以更安全、更可靠地將夥伴連接到重要供應鏈商務程序。  
  
 TPM 方案搭配 EDI 和 AS2 支援用於管理中的交易夥伴提供功能強大且可擴充的解決方案[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 本節中的主題 (和下方所列的其他主題) 對於 TPM 和如何使用 TPM 來管理交易夥伴，提供了高階概觀。 這些主題也提供了關於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 如何執行 EDI 和 AS2 處理的說明。  
  
## <a name="in-this-section-and-more-good-info"></a>在本節與良好的詳細資訊

**了解，開始使用，和教學課程**  

-   [交易夥伴管理解決方案的建置區塊](../core/building-blocks-of-a-trading-partner-management-solution.md)  
  
-   [BizTalk Server EDI 功能](../core/biztalk-server-edi-functionality.md)  
  
-   [BizTalk Server AS2 功能](../core/biztalk-server-as2-functionality.md)  

- [EDI 和 AS2 解決方案架構](../core/edi-and-as2-solution-architecture.md)

-   [環境最佳化的後續設定步驟](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md) 

- [EDI、AS2 和 EDIFACT 的教學課程和逐步解說](../core/tutorials-and-walkthroughs-for-edi-as2-and-edifact.md)


**深入了解在建立 EDI 和 AS2 解決方案**
- [建立 EDI 和 AS2 成品](../core/managing-edi-and-as2-solutions.md)

- [開發和設定 BizTalk Server EDI 解決方案](../core/developing-and-configuring-biztalk-server-edi-solutions.md)

- [開發和設定 BizTalk Server AS2 解決方案](../core/developing-and-configuring-biztalk-server-as2-solutions.md)

-   [EDI 和 AS2 SDK 的範例）](../core/edi-and-as2-biztalk-server-samples-folder.md)  


 **使用繫結檔案**  

- [使用繫結檔案匯入或匯出為新的 BizTalk Server 2016](../core/use-binding-files-to-import-or-export.md)  

-   [如何匯出 EDI-AS2 解決方案的繫結](../core/how-to-export-bindings-for-an-edi-as2-solution.md)  
  
-   [如何匯入 EDI-AS2 解決方案的繫結](../core/how-to-import-bindings-for-an-edi-as2-solution.md)  
  
-   [自訂繫結檔案](../core/customizing-binding-files.md)  


**監視和疑難排解**

- [監控 EDI 和 AS2 解決方案](../core/monitoring-edi-and-as2-solutions.md)

- [疑難排解 EDI 和 AS2 解決方案](../core/troubleshooting-edi-and-as2-solutions.md)
  
- 檢視 詳細資料 [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] 
  
- [EDI 和 AS2 事件與錯誤](../core/edi-and-as2-events-and-errors.md)
 


  
