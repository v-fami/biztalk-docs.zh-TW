---
title: 設定 Oracle 資料庫配接器的 Oracle 用戶端 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- net service name
- tnsnames.ora
- configuring, the Oracle client
- connect descriptor
- Oracle client, configuring
- Oracle Net Configuration Assistant
- Oracle Net Configuration Assistant, using the
ms.assetid: 2d4c0f20-b3a6-453f-a9b3-65fd5a38c020
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 209d5603a9f8ff8c09185093efb976afb6432d65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214110"
---
# <a name="configure-the-oracle-client-for-the-oracle-database-adapter"></a><span data-ttu-id="f92f6-102">設定 Oracle 資料庫配接器的 Oracle 用戶端</span><span class="sxs-lookup"><span data-stu-id="f92f6-102">Configure the Oracle Client for the Oracle Database adapter</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="f92f6-103">本主題是您用來連接到 Oracle 資料庫 tnsnames.ora 時才適用。</span><span class="sxs-lookup"><span data-stu-id="f92f6-103">This topic is relevant only if you are using tnsnames.ora to connect to the Oracle database.</span></span>  
  
 <span data-ttu-id="f92f6-104">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]會連接到 Oracle 資料庫，透過您的電腦上安裝 Oracle 用戶端。</span><span class="sxs-lookup"><span data-stu-id="f92f6-104">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] connects to the Oracle database through the Oracle client installed on your computer.</span></span> <span data-ttu-id="f92f6-105">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]網路服務名稱將其傳遞您指定連線 URI Oracle 用戶端，以連接到 Oracle 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="f92f6-105">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] passes the net service name that you specify in the connection URI to the Oracle client to establish a connection to the Oracle database.</span></span> <span data-ttu-id="f92f6-106">網路服務名稱是用來取得目標 Oracle 資料庫服務的連接資訊的 Oracle 用戶端的別名。</span><span class="sxs-lookup"><span data-stu-id="f92f6-106">The net service name is an alias that the Oracle client uses to acquire connection information for the target Oracle database service.</span></span>  
  
 <span data-ttu-id="f92f6-107">網路服務的名稱是根據命名的方法而設定為使用 Oracle 用戶端解析。</span><span class="sxs-lookup"><span data-stu-id="f92f6-107">The Oracle client resolves the net service name according to the naming method that it is configured to use.</span></span> <span data-ttu-id="f92f6-108">您使用 Oracle Net Configuration Assistant 設定 Oracle 用戶端所使用的命名方法。</span><span class="sxs-lookup"><span data-stu-id="f92f6-108">You use the Oracle Net Configuration Assistant to configure the naming methods to be used by the Oracle client.</span></span> <span data-ttu-id="f92f6-109">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援連接到 Oracle 資料庫的本機命名方法。</span><span class="sxs-lookup"><span data-stu-id="f92f6-109">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports the Local Naming method for connecting to the Oracle database.</span></span> <span data-ttu-id="f92f6-110">這個方法會使用本機檔案，tnsnames.ora，解析網路服務名稱。</span><span class="sxs-lookup"><span data-stu-id="f92f6-110">This method uses a local file, tnsnames.ora, to resolve the net service name.</span></span>  
  
 <span data-ttu-id="f92f6-111">Tnsnames.ora 檔案關聯網路服務名稱與連接描述元包含 Oracle 用戶端必須連接到特定的 Oracle 資料庫服務 （執行個體） 的資訊。</span><span class="sxs-lookup"><span data-stu-id="f92f6-111">The tnsnames.ora file associates net service names with connect descriptors that contain the information the Oracle client needs to establish a connection to a specific Oracle database service (instance).</span></span> <span data-ttu-id="f92f6-112">以下是從 tnsnames.ora 範例項目。</span><span class="sxs-lookup"><span data-stu-id="f92f6-112">The following is a sample entry from tnsnames.ora.</span></span>  
  
```  
ADAPTER =  
  (DESCRIPTION =  
    (ADDRESS_LIST =  
      (ADDRESS = (PROTOCOL = TCP)(HOST = yourOracleServer)(PORT = 1521))  
    )  
    (CONNECT_DATA =  
      (SERVICE_NAME = yourOracleDatabaseServiceName)  
    )  
  )  
```  
  
 <span data-ttu-id="f92f6-113">在此範例項目，配接器是網路服務名稱。</span><span class="sxs-lookup"><span data-stu-id="f92f6-113">In this sample entry, ADAPTER is the net service name.</span></span> <span data-ttu-id="f92f6-114">連接描述元指定位址資訊和使用配接器相關聯的 Oracle 資料庫服務的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="f92f6-114">The connect descriptor specifies address information and the service name of the Oracle database service associated with ADAPTER.</span></span> <span data-ttu-id="f92f6-115">您可以使用 Oracle Net Configuration Assistant 來建立及設定 tnsnames.ora 以網路服務名稱。</span><span class="sxs-lookup"><span data-stu-id="f92f6-115">You can use the Oracle Net Configuration Assistant to create and configure net service names in tnsnames.ora.</span></span> <span data-ttu-id="f92f6-116">設定網路服務名稱之後，您可以如下列範例所示的連線 URI 中指定它。</span><span class="sxs-lookup"><span data-stu-id="f92f6-116">After you have configured the net service name, you can specify it in a connection URI as in the following example.</span></span>  
  
```  
oracledb://ADAPTER  
```  
  
 <span data-ttu-id="f92f6-117">如需有關使用 Oracle Net Configuration Assistant 以及 tnsnames.ora 有關的詳細資訊，請參閱 Oracle 資料庫網路服務系統管理員指南。</span><span class="sxs-lookup"><span data-stu-id="f92f6-117">For more information about using the Oracle Net Configuration Assistant and about tnsnames.ora, see the Oracle Database Net Services Administrator's Guide.</span></span> <span data-ttu-id="f92f6-118">特定的安裝，請參閱您的資料庫管理員的相關設定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f92f6-118">Consult your database administrator about configuration details for your specific installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f92f6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f92f6-119">See Also</span></span>  
[<span data-ttu-id="f92f6-120">建立 Oracle 資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="f92f6-120">Create a connection to the Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)