---
title: 連接到使用 SQL 配接器的 Visual Studio 中的 SQL Server |Microsoft 文件
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
ms.openlocfilehash: bb5e2d149c9a9533e4bec3c2c1c435bffb3adf26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222806"
---
# <a name="connect-to-sql-server-in-visual-studio-using-the-sql-adapter"></a>連接到使用 SQL 配接器的 Visual Studio 中的 SQL Server
本節提供有關如何使用指示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]、 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，而[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
-    **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]** 位於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案，並已安裝的一部分[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。 您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。 如需開發使用 BizTalk Server 解決方案的詳細資訊，請參閱[開發 BizTalk 應用程式使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)。  
  
-    **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]** 位於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案，並已安裝的一部分[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝。 您使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。 如需詳細資訊，關於開發方案與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[開發 BizTalk 應用程式使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)。  
  
    > [!NOTE]
    >  因為[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開為 WCF 自訂繫結和做為 BizTalk 配接器，您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]從 BizTalk 專案連接到 SQL Server。  
  
-    **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** 用於非 BizTalk 開發專案。 您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 用戶端類別或 WCF 服務的回呼介面，當您開發使用 WCF 服務模型的解決方案。 如需有關開發 WCF 服務模型的方案的詳細資訊，請參閱[開發 SAP 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)。  
  
 若要使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，您必須先連接到 SQL Server。 這三個方法會顯示的對話方塊，您可以透過此設定的連接來設定下列：  
  
-   **連接參數**。 這些是用來建置連接 URI，例如 SQL Server 名稱、 資料庫執行個體名稱和資料庫名稱的參數。  
  
-   **適用於 SQL Server 的使用者名稱密碼認證**。 這些用來建立連線時讓您驗證 SQL Server 上。 您必須指定使用者名稱和密碼。  
  
-   **繫結屬性**。 繫結屬性是選擇性的及您是否指定取決於主要是否您需要設定特定的繫結屬性的作業為目標。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
 最小值，當您設定連接到 SQL Server，您只需要指定繫結內容和需要的連線，並會影響所傳回的中繼資料的連接參數[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]您想要的作業目標。 不過，您也可以指定任何其他繫結屬性與將在執行階段使用的連接參數的值。 這是因為：  
  
-   [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]繫結屬性和您指定當您設定的連接，並將這個檔案加入專案的連接參數建立 BizTalk 連接埠繫結檔案。  
  
-   [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]從繫結屬性和您指定當您設定的連接，並將這個檔案加入您的專案目錄中的連接屬性，建立 app.config 檔案。  
  
