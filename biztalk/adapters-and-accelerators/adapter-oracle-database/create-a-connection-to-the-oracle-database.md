---
title: 建立 Oracle 資料庫的連接 |Microsoft Docs
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
ms.openlocfilehash: c79af51280879e1cf6c72053a42822cd24fae68e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988455"
---
# <a name="create-a-connection-to-the-oracle-database"></a>建立 Oracle 資料庫的連接
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 因此，它可讓 Oracle 資料庫，透過 WCF 端點位址的通訊。 在 WCF 中，端點位址通常被表示做為統一資源識別元 (URI)，用來識別服務的網路位置。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]表示此位置做為連線 URI，其中包含屬性的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]用以連接到 Oracle 資料庫。  
  
 您必須指定 URI 的連接時您：  
  
- 建立通道處理站或通道接聽程式，使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型，或當您建立使用 WCF 用戶端或服務主機[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型。  
  
- 建立實體連接埠繫結中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。  
  
- 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]來產生 WCF 用戶端類別或 WCF 服務介面[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型方案。  
  
- 使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]來擷取從訊息結構描述[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。  
  
- 您可以使用 ServiceModel Metadata Utility 工具 (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務模型方案的 WCF 服務介面。  
  
  [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援兩種方式來建立 Oracle 資料庫的連接：  
  
- **使用 tnsnames.ora**。 這種方法，連線配接器用戶端所提供的 URI 會包含只 tnsnames.ora 檔案中指定的網路服務名稱。 配接器會擷取連線參數，例如伺服器名稱、 服務名稱、 連接埠不會，從檔案中的 net 的服務名稱項目等等。 若要使用這種方法，執行 Oracle 用戶端的電腦，必須設定為包含 tnsnames.ora 檔案中的 net 的服務名稱的 Oracle 資料庫中。  
  
  > [!IMPORTANT]
  >  執行 Oracle 用戶端的限制，因為**DataSourceName**中的參數 （net 的服務名稱）[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)不能包含超過 39 個字元，如果您正在執行在交易中的作業。 因此，請確定為指定的值**DataSourceName**參數是否小於或等於 39 個字元，如果您將會在交易中執行作業。  
  
- **不使用 tnsnames.ora**。 在此方法中，配接器用戶端會指定連線參數，直接在 連線 URI 中。 這不需要網路的服務名稱會出現在用戶端電腦上的 tnsnames.ora 檔案。 這種方法甚至不需要 tnsname.ora 檔案必須存在於用戶端電腦上。  
  
  > [!IMPORTANT]
  >  如果您要在交易中執行作業，則不支援這種連線模式。 這是因為 Oracle 用戶端的限制。  
  
  在本節中的主題描述如何之間建立連線[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]和 Oracle 資料庫，藉由提供您使用：  
  
- 設定 Oracle 用戶端的相關資訊。  
  
- 連接屬性和 Oracle 連接 URI 的結構資訊。  
  
- 示範如何建立連接所使用的主題連結[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
- 連接到 Oracle 資料庫使用 Windows 驗證的相關資訊。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [設定 Oracle 用戶端，Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)  
  
-   [建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)  
  
-   [連接到 Oracle 資料庫使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)  
  
## <a name="see-also"></a>另請參閱  
[開發您的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)