---
title: 連接到使用 SQL 配接器的 Visual Studio 中的 SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62fc2c01-6e4d-4b3b-8581-1d57436ef4e9
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22e527714bb1cf14531a6565cd7987531a4eb07b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014503"
---
# <a name="connect-to-sql-server-in-visual-studio-using-the-sql-adapter"></a>連接到 SQL Server，在 Visual Studio 中使用 SQL 配接器
本節提供有關如何使用指示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
- **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]** 位於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案，並已安裝的一部分[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。 您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。 如需有關如何使用 BizTalk Server 開發解決方案的詳細資訊，請參閱 <<c0> [ 使用 SQL 配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)。  
  
- **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]** 位於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案，並已安裝的一部分[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝。 您使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。 如需有關使用開發解決方案[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 使用 SQL 配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)。  
  
  > [!NOTE]
  >  因為[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開為 WCF 自訂繫結和 BizTalk 配接器，您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]從 BizTalk 專案，以連接到 SQL Server。  
  
- **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** 用於非 BizTalk 的程式設計專案。 您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來開發使用 WCF 服務模型的方案時，產生 WCF 用戶端類別或 WCF 服務的回呼介面。 如需有關如何使用 WCF 服務模型開發解決方案的詳細資訊，請參閱 <<c0> [ 開發的 SAP 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)。  
  
  若要使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，您必須先連接到 SQL Server。 這三種方式呈現一個對話方塊，您可以透過此設定的連接來設定下列所示：  
  
- **連接參數**。 這些是用來建置連接 URI，例如 SQL Server 名稱、 資料庫執行個體名稱和資料庫名稱的參數。  
  
- **適用於 SQL Server 的使用者名稱密碼認證**。 這些用來驗證您在 SQL Server 上建立連線時。 您必須指定使用者名稱和密碼。  
  
- **繫結屬性**。 繫結屬性是選擇性的以及您是否指定主要取決於是否您目標需要設定特定的繫結屬性的作業。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
  最小值，當您設定連線到 SQL Server，您只需要指定繫結屬性和連接參數，才能建立連線，以及影響所傳回的中繼資料[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]您想要的作業目標。 不過，您也可以指定任何其他繫結屬性與將在執行階段使用的連接參數的值。 這是因為：  
  
- [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]從您指定當您設定的連接，並將此檔案加入至您專案的連接參數與繫結屬性建立 BizTalk 連接埠繫結檔案。  
  
- [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]從您指定當您設定的連接，並將此檔案加入您的專案目錄中的連接屬性與繫結屬性建立 app.config 檔案。  
  
