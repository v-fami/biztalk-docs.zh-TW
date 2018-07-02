---
title: 開始使用 BizTalk Adapter for mySAP Business Suite |Microsoft Docs
description: 安裝自訂 Rfc、 了解配接器、 完成上逐步教學課程，以使用 mySAP 配接器的 BizTalk 配接器組件 (BAP) 中執行 SAP RFC 和 IDOC 工作
ms.custom: ''
ms.date: 08/16/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e2013253-f911-4e35-a33a-b4a9bcb136aa
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02112b6974a537c9f66cc301014ae16bb4bf326f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967465"
---
# <a name="get-started-with-the-biztalk-adapter-for-mysap-business-suite"></a>開始使用 BizTalk Adapter for mySAP Business Suite
本節的是 Microsoft 的新手的使用者提供的配接器、 必要條件和主題概觀[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 它討論的功能[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]以及可對使用配接器的 SAP 系統的不同作業。  

## <a name="what-is-an-adapter"></a>何謂配接器？ 
配接器是一種軟體元件，可讓您傳送和接收訊息的營運 (LOB) 系統。 配接器的主要設計目的是協助交易夥伴之間的商務文件的交換。 由於每個商務系統可能會遵守特定的文件格式和通訊協定，配接器必須使用傳遞機制符合普遍認可的標準和通訊協定，來為使用者提供統一的介面。  
  
 配接器可以分成兩大類：  
  
- **LOB 配接器**。 這類配接器提供服務導向程式設計模型，以存取 LOB 系統，例如 SAP 或 Siebel 配接器。  
  
- **資料配接器**。 這類配接器提供服務導向程式設計模型，以存取資料庫 — 比方說，針對 SQL Server 的 Oracle 資料庫配接器。  
  
  有五個配接器在[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:  
  
- [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] ( [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])  
  
- [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] ( [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])  
  
- [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] ( [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])  
  
- [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] ( [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)])，包括[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)])  
  
- [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] ( [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)])，包括[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])  
  
  > [!NOTE]
  >  [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不適用於 64 位元平台。  
  
  如果您沒有已經知道您要使用的方式[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在您的公司，建議您開始探索功能，以及配接器功能中所述[了解 BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md).  
  
## <a name="next-steps"></a>後續的步驟  
- [安裝 Data Provider for SAP 的自訂 RFC](install-custom-rfcs-for-the-data-provider-for-sap.md)
  
-   [了解 BizTalk Adapter for mySAP Business Suite](understand-biztalk-adapter-for-mysap-business-suite.md)  

- [在 SAP 上完成 RFC 和 IDOC 工作](performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)
  
-   [SAP 配接器教學課程](sap-adapter-tutorials.md)  