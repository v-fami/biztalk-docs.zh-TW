---
title: "連接至 BizTalk Server 與 SQL Server 永遠加密的資料行 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fcc20a2b-daf9-4b7f-ae61-cb408e4bd04c
caps.latest.revision: "4"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 62b570fabda6a0e46f87c36b863e2b99e464020b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-sql-server-always-encrypted-columns-with-biztalk-server"></a>連接至 BizTalk Server 與 SQL Server 永遠加密的資料行
在 WCF-SQL 配接器中啟用 永遠加密[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]查詢加密資料行。  

**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，WCF-SQL 配接器可以查詢加密資料行中的[!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)]。 `ColumnEncryptionSetting`繫結屬性用來啟用或停用 永遠加密的資料庫從取得解密/加密資料行值的功能。

本主題說明如何啟用或停用此功能[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。

> [!TIP] 
> [永遠加密 (Database Engine)](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine)是絕佳的資源，了解，並深入了解[!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)]功能。

## <a name="prerequisites"></a>必要條件
安裝[功能套件 1](https://www.microsoft.com/download/details.aspx?id=55100)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。

## <a name="enable-always-encrypted"></a>啟用永遠加密

1. 在**BizTalk Server 管理**主控台，以滑鼠右鍵按一下您的 WCF SQL 連接埠，然後選取**屬性**。
2. 移至**繫結** 索引標籤。
3. 在下**永遠加密**、 啟用或停用`ColumnEncryptionSettings`屬性：

* **啟用**： 連接埠查詢，並取得加密的資料，從 永遠加密的資料庫
* **已停用**： 連接埠查詢永遠加密資料庫，但傳回的資料會雜湊

    ![啟用永遠加密](../core/media/enable-always-encrypted.png)

4. 選取**套用**，和**確定**以儲存變更。

## <a name="see-also"></a>另請參閱
[一律加密 (Database Engine)](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine)  
[設定此功能套件](../core/configure-the-feature-pack.md)