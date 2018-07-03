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
# <a name="connect-to-sql-server-always-encrypted-columns-with-biztalk-server"></a><span data-ttu-id="f4b67-102">連接至 SQL Server Always Encrypted 資料行，與 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="f4b67-102">Connect to SQL Server Always Encrypted columns with BizTalk Server</span></span>
<span data-ttu-id="f4b67-103">中的 WCF-SQL 配接器中啟用 Always Encrypted[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]查詢加密資料行。</span><span class="sxs-lookup"><span data-stu-id="f4b67-103">Enable Always Encrypted in the WCF-SQL adapter in [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] to query encrypted columns.</span></span>  

<span data-ttu-id="f4b67-104">**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，WCF-SQL 配接器可以查詢加密資料行中的[!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f4b67-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, the WCF-SQL adapter can query encrypted columns in [!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="f4b67-105">`ColumnEncryptionSetting`繫結屬性用來啟用或停用 Always Encrypted 的資料庫從取得解密/加密資料行值的功能。</span><span class="sxs-lookup"><span data-stu-id="f4b67-105">The `ColumnEncryptionSetting` binding property is used to enable or disable the functionality to get decrypted/encrypted column values from an Always Encrypted database.</span></span>

<span data-ttu-id="f4b67-106">本主題說明如何啟用或停用這項功能[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f4b67-106">This topic shows you how to enable or disable this feature in [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span>

> [!TIP]
> <span data-ttu-id="f4b67-107">[Always Encrypted （資料庫引擎）](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine)是絕佳的資源來了解並深入了解[!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="f4b67-107">[Always Encrypted (Database Engine)](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) is a great resource to understand and learn more about this [!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)] feature.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f4b67-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="f4b67-108">Prerequisites</span></span>
<span data-ttu-id="f4b67-109">安裝[Feature Pack 2](https://aka.ms/bts2016fp2)在您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f4b67-109">Install [Feature Pack 2](https://aka.ms/bts2016fp2) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span>

## <a name="enable-always-encrypted"></a><span data-ttu-id="f4b67-110">啟用 Always Encrypted</span><span class="sxs-lookup"><span data-stu-id="f4b67-110">Enable Always Encrypted</span></span>

1. <span data-ttu-id="f4b67-111">在 [ **BizTalk Server 管理]** 主控台，以滑鼠右鍵按一下您的 WCF SQL 連接埠，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="f4b67-111">In the **BizTalk Server Administration** console, right-click your WCF-SQL port, and select **Properties**.</span></span>
2. <span data-ttu-id="f4b67-112">移至**繫結** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f4b67-112">Go to the **Binding** tab.</span></span>
3. <span data-ttu-id="f4b67-113">底下**Always Encrypted**、 啟用或停用`ColumnEncryptionSettings`屬性：</span><span class="sxs-lookup"><span data-stu-id="f4b67-113">Under **Always Encrypted**, enable or disable the `ColumnEncryptionSettings` property:</span></span>

* <span data-ttu-id="f4b67-114">**啟用**： 連接埠查詢，並取得加密的資料，從 Always Encrypted 的資料庫</span><span class="sxs-lookup"><span data-stu-id="f4b67-114">**Enabled**: The port queries, and gets encrypted data from an Always Encrypted database</span></span>
* <span data-ttu-id="f4b67-115">**已停用**: 連接埠查詢的 Always Encrypted 的資料庫，但傳回的資料會進行雜湊</span><span class="sxs-lookup"><span data-stu-id="f4b67-115">**Disabled**: The port queries the Always Encrypted database, but the data returned is hashed</span></span>

    ![啟用 Always Encrypted](../core/media/enable-always-encrypted.png)

4. <span data-ttu-id="f4b67-117">選取 **套用**，並**確定**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="f4b67-117">Select **Apply**, and **OK** to save your changes.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4b67-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4b67-118">See also</span></span>
[<span data-ttu-id="f4b67-119">Always Encrypted (資料庫引擎)</span><span class="sxs-lookup"><span data-stu-id="f4b67-119">Always Encrypted (Database Engine)</span></span>](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine)  
[<span data-ttu-id="f4b67-120">設定 Feature Pack</span><span class="sxs-lookup"><span data-stu-id="f4b67-120">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)