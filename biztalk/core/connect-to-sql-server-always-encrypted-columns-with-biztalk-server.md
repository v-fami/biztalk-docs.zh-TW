---
title: 連接至 SQL Server Always Encrypted 資料行，與 BizTalk Server |Microsoft Docs
ms.custom: ''
ms.date: 11/20/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fcc20a2b-daf9-4b7f-ae61-cb408e4bd04c
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fd02a1c89b3c308fc853dde8b541d23aa999053
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008551"
---
# <a name="connect-to-sql-server-always-encrypted-columns-with-biztalk-server"></a>連接至 SQL Server Always Encrypted 資料行，與 BizTalk Server
中的 WCF-SQL 配接器中啟用 Always Encrypted[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]查詢加密資料行。  

**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，WCF-SQL 配接器可以查詢加密資料行中的[!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)]。 `ColumnEncryptionSetting`繫結屬性用來啟用或停用 Always Encrypted 的資料庫從取得解密/加密資料行值的功能。

本主題說明如何啟用或停用這項功能[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。

> [!TIP]
> [Always Encrypted （資料庫引擎）](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine)是絕佳的資源來了解並深入了解[!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)]功能。

## <a name="prerequisites"></a>必要條件
安裝[Feature Pack 2](https://aka.ms/bts2016fp2)在您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。

## <a name="enable-always-encrypted"></a>啟用 Always Encrypted

1. 在 [ **BizTalk Server 管理]** 主控台，以滑鼠右鍵按一下您的 WCF SQL 連接埠，然後選取**屬性**。
2. 移至**繫結** 索引標籤。
3. 底下**Always Encrypted**、 啟用或停用`ColumnEncryptionSettings`屬性：

* **啟用**： 連接埠查詢，並取得加密的資料，從 Always Encrypted 的資料庫
* **已停用**: 連接埠查詢的 Always Encrypted 的資料庫，但傳回的資料會進行雜湊

    ![啟用 Always Encrypted](../core/media/enable-always-encrypted.png)

4. 選取 **套用**，並**確定**以儲存變更。

## <a name="see-also"></a>另請參閱
[Always Encrypted (資料庫引擎)](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine)  
[設定 Feature Pack](../core/configure-the-feature-pack.md)