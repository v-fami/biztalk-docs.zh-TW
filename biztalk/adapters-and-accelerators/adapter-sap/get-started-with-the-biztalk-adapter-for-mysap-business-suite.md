---
title: "開始使用 BizTalk Adapter for mySAP Business Suite |Microsoft 文件"
description: "安裝自訂 Rfc、 了解配接器、 完成上逐步教學課程，可使用 mySAP 配接器的 BizTalk 配接器組件 (BAP) 中執行 SAP RFC 和 IDOC 工作"
ms.custom: 
ms.date: 08/16/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2013253-f911-4e35-a33a-b4a9bcb136aa
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e5607a255f50bf5295d4ea22c9a680d86f38e5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="get-started-with-the-biztalk-adapter-for-mysap-business-suite"></a>開始使用 BizTalk Adapter for mySAP Business Suite
本節提供使用者熟悉 Microsoft 配接器、 必要條件和主題的總覽[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 其中也會討論的功能[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]以及可對使用配接器的 SAP 系統的不同作業。  

## <a name="what-is-an-adapter"></a>什麼是配接器？ 
配接器是可讓您傳送和接收訊息的特定業務 (LOB) 系統的軟體元件。 配接器的主要設計目的是協助交易夥伴之間的商務文件的交換。 因為每個商務系統可能會遵守特定的文件格式和通訊協定，配接器必須使用的傳遞機制符合普遍認可的標準和通訊協定，來為使用者提供統一的介面。  
  
 配接器可以分成兩大類別：  
  
-   **LOB 配接器**。 這類配接器提供的服務導向程式設計模型，以存取 LOB 系統，例如 SAP 或 Siebel 配接器。  
  
-   **資料配接器**。 這類配接器可提供服務導向程式設計模型，access 資料庫 — 比方說，針對 SQL Server 的 Oracle 資料庫配接器。  
  
 有五個配接器在[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:  
  
-   [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] ( [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])  
  
-   [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] ( [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])  
  
-   [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] ( [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])  
  
-   [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] ( [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)])，包括[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)])  
  
-   [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] ( [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)])，包括[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])  
  
    > [!NOTE]
    >  [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不適用於 64 位元平台。  
  
 如果您不已經知道您要使用的方式[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在您的公司，建議您一開始會瀏覽功能，以及配接器功能中所述[了解 BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md).  
  
## <a name="next-steps"></a>後續的步驟  
- [安裝適用於 SAP 的資料提供者的自訂 Rfc](install-custom-rfcs-for-the-data-provider-for-sap.md)
  
-   [瞭解 BizTalk Adapter for mySAP Business Suite](understand-biztalk-adapter-for-mysap-business-suite.md)  

- [完成上 SAP RFC 和 IDOC 工作](performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)
  
-   [SAP 配接器教學課程](sap-adapter-tutorials.md)  