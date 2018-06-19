---
title: 建立連接到 Oracle 資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapter, connecting to the Oracle Database
ms.assetid: 95f7905a-abad-4841-85c4-62cf0cc1e044
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f9a42994f0cde9df19e3b80e16fcbafbb2d8d5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214966"
---
# <a name="create-a-connection-to-the-oracle-database"></a>建立 Oracle 資料庫的連接
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 因此，它可讓 Oracle 資料庫，透過 WCF 端點位址的通訊。 在 WCF 中，端點位址通常表示做為統一資源識別元 (URI)，用來識別服務的網路位置。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]表示這個位置做為連接 URI，其中包含屬性的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]用以連接到 Oracle 資料庫。  
  
 您必須指定連線 URI 時您：  
  
-   建立通道處理站或通道接聽程式使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型，或當您建立使用 WCF 用戶端或服務主機[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型。  
  
-   建立實體連接埠繫結中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案。  
  
-   使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別或 WCF 服務介面[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型方案。  
  
-   使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]擷取訊息結構描述從[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案。  
  
-   您可以使用 ServiceModel Metadata Utility 工具 (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務模型方案的 WCF 服務介面。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援兩種方式建立連接到 Oracle 資料庫：  
  
-   **使用 tnsnames.ora**。 這種方法，連線配接器用戶端所提供的 URI 包含只 tnsnames.ora 檔案中指定的網路服務名稱。 配接器會擷取連線參數，例如伺服器名稱、 服務名稱，連接埠編號，從檔案中的網路服務名稱的項目等等。 若要使用這種方法，執行 Oracle 用戶端的電腦必須設定要在 tnsnames.ora 檔案中包含之 Oracle 資料庫的網路服務名稱。  
  
    > [!IMPORTANT]
    >  由於 Oracle 用戶端的限制， **DataSourceName**中的參數 (net service name)[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)不能包含超過 39 個字元，如果您正在執行在交易中的作業。 因此，請確定為指定的值**DataSourceName**參數為小於或等於 39 個字元，如果您將在交易中執行的作業。  
  
-   **不使用 tnsnames.ora**。 在這種方式，配接器用戶端會指定直接在 連線 URI 中的連接參數。 這不需要網路服務名稱必須存在於用戶端電腦上 tnsnames.ora 檔案。 這個方法甚至不需要 tnsname.ora 檔案存在於用戶端電腦上。  
  
    > [!IMPORTANT]
    >  如果您在交易中執行作業，則不支援這種連線模式。 這是因為 Oracle 用戶端的限制。  
  
 此章節的主題描述如何之間建立連線[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]和 Oracle 資料庫，藉由提供您具有：  
  
-   設定 Oracle 用戶端的相關資訊。  
  
-   連接屬性和結構的 Oracle 連接 URI 的相關資訊。  
  
-   示範如何建立連接所使用的主題連結[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
-   連接到 Oracle 資料庫使用 Windows 驗證的相關資訊。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [設定 Oracle 資料庫配接器的 Oracle 用戶端](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)  
  
-   [建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)  
  
-   [連接到 Oracle 資料庫使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)  
  
## <a name="see-also"></a>另請參閱  
[開發應用程式的 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)