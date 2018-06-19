---
title: 取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata, retrieving in Visual Studio
- metadata
ms.assetid: d903b408-1144-4625-909d-710826e37769
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fdf1d1943c471591e35f1efb6ca6e08f36948fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214326"
---
# <a name="get-metadata-for-oracle-database-operations-in-visual-studio"></a>取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]提供三個[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可用來協助您開發解決方案使用配接器的元件。  
  
-   [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]和[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]會出現在 BizTalk Server 專案。 您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]和[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。 如需開發使用 BizTalk Server 解決方案的詳細資訊，請參閱[開發 BizTalk 應用程式使用 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)  
  
-   [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]用於非 BizTalk 開發專案。 您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 用戶端類別或 WCF 服務的回呼介面，當您開發使用 WCF 服務模型的解決方案。 如需有關開發 WCF 服務模型的方案的詳細資訊，請參閱[開發 Oracle 資料庫應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)。  
  
 所有這三個[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]元件簡化開發：  
  
-   提供的 Microsoft Windows 介面，您可以瀏覽和搜尋您想要使用您的方案中的作業。  
  
-   正在擷取這些目標作業的配接器所公開的中繼資料。  
  
-   轉換的中繼資料，這表示做為 Web 服務描述語言 (WSDL) 文件，配接器，成您可以使用您的方案 （BizTalk 專案的 XSD 訊息結構描述或 WCF 服務合約的.NET 物件表示法中的表單服務模型） 並將它加入至您的專案。  
  
 本節提供有關如何使用指示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [連接到 Oracle 資料庫，在 Visual Studio 中使用 取用配接器服務](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md) 
  
-   [瀏覽、 搜尋和 Oracle 資料庫作業，取得中繼資料](../../adapters-and-accelerators/adapter-oracle-database/browse-search-and-get-metadata-for-oracle-database-operations.md)  
  
## <a name="see-also"></a>另請參閱  
[開發應用程式的 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)