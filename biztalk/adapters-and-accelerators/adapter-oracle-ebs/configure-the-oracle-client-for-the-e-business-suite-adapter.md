---
title: "設定 Oracle E-business Suite 配接器用戶端 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 842b6ecc-5334-4cc0-af10-baa7f692ad23
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ada64bf6f54c95f3d6e1c8f968a506476dbbc6fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-oracle-client-for-the-e-business-suite-adapter"></a><span data-ttu-id="14f8c-102">設定 Oracle E-business Suite 配接器用戶端</span><span class="sxs-lookup"><span data-stu-id="14f8c-102">Configure the Oracle client for the E-Business Suite adapter</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="14f8c-103">本主題是您用來連接到 Oracle 資料庫 tnsnames.ora 時才適用。</span><span class="sxs-lookup"><span data-stu-id="14f8c-103">This topic is relevant only if you are using tnsnames.ora to connect to the Oracle database.</span></span>  
  
 <span data-ttu-id="14f8c-104">若要連接到[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]，配接器連接到電腦上安裝 Oracle 用戶端透過基礎的 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="14f8c-104">To establish a connection to the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)], the adapter connects to the underlying Oracle database through the Oracle client installed on your computer.</span></span> <span data-ttu-id="14f8c-105">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]網路服務名稱將其傳遞您在 Oracle 用戶端，以連接到 Oracle E-business Suite 連線 URI 中指定。</span><span class="sxs-lookup"><span data-stu-id="14f8c-105">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] passes the net service name that you specify in the connection URI to the Oracle client to establish a connection to Oracle E-Business Suite.</span></span> <span data-ttu-id="14f8c-106">網路服務名稱是用來取得目標 Oracle 資料庫服務的連接資訊的 Oracle 用戶端的別名。</span><span class="sxs-lookup"><span data-stu-id="14f8c-106">The net service name is an alias that the Oracle client uses to acquire connection information for the target Oracle database service.</span></span>  
  
 <span data-ttu-id="14f8c-107">網路服務的名稱是根據命名的方法而設定為使用 Oracle 用戶端解析。</span><span class="sxs-lookup"><span data-stu-id="14f8c-107">The Oracle client resolves the net service name according to the naming method that it is configured to use.</span></span> <span data-ttu-id="14f8c-108">您使用 Oracle Net Configuration Assistant 設定 Oracle 用戶端所使用的命名方法。</span><span class="sxs-lookup"><span data-stu-id="14f8c-108">You use the Oracle Net Configuration Assistant to configure the naming methods to be used by the Oracle client.</span></span> <span data-ttu-id="14f8c-109">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]連接到 Oracle E-business Suite 支援本機命名的方法。</span><span class="sxs-lookup"><span data-stu-id="14f8c-109">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports the Local Naming method for connecting to Oracle E-Business Suite.</span></span> <span data-ttu-id="14f8c-110">這個方法會使用本機檔案，tnsnames.ora，解析網路服務名稱。</span><span class="sxs-lookup"><span data-stu-id="14f8c-110">This method uses a local file, tnsnames.ora, to resolve the net service name.</span></span>  
  
 <span data-ttu-id="14f8c-111">Tnsnames.ora 檔案關聯網路服務名稱與連接描述元包含 Oracle 用戶端需要連接到特定的 Oracle 資料庫服務 （執行個體） 的資訊。</span><span class="sxs-lookup"><span data-stu-id="14f8c-111">The tnsnames.ora file associates net service names with connect descriptors that contain the information that the Oracle client needs to establish a connection to a specific Oracle database service (instance).</span></span> <span data-ttu-id="14f8c-112">以下是從 tnsnames.ora 範例項目。</span><span class="sxs-lookup"><span data-stu-id="14f8c-112">The following is a sample entry from tnsnames.ora.</span></span>  
  
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
  
 <span data-ttu-id="14f8c-113">在此範例項目，配接器是網路服務名稱。</span><span class="sxs-lookup"><span data-stu-id="14f8c-113">In this sample entry, ADAPTER is the net service name.</span></span> <span data-ttu-id="14f8c-114">連接描述元指定位址資訊和使用配接器相關聯的 Oracle 資料庫服務的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="14f8c-114">The connect descriptor specifies address information and the service name of the Oracle database service associated with ADAPTER.</span></span> <span data-ttu-id="14f8c-115">您可以使用 Oracle Net Configuration Assistant 來建立及設定 tnsnames.ora 以網路服務名稱。</span><span class="sxs-lookup"><span data-stu-id="14f8c-115">You can use the Oracle Net Configuration Assistant to create and configure net service names in tnsnames.ora.</span></span> <span data-ttu-id="14f8c-116">設定網路服務名稱之後，您可以如下列範例所示的連線 URI 中指定它。</span><span class="sxs-lookup"><span data-stu-id="14f8c-116">After you have configured the net service name, you can specify it in a connection URI as in the following example.</span></span>  
  
```  
oracleebs://ADAPTER  
```  
  
 <span data-ttu-id="14f8c-117">如需有關使用 Oracle Net Configuration Assistant 以及 tnsnames.ora 有關的詳細資訊，請參閱 Oracle 資料庫網路服務系統管理員指南。</span><span class="sxs-lookup"><span data-stu-id="14f8c-117">For more information about using the Oracle Net Configuration Assistant and about tnsnames.ora, see the Oracle Database Net Services Administrator's Guide.</span></span> <span data-ttu-id="14f8c-118">特定的安裝，請參閱您的資料庫管理員的相關設定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="14f8c-118">Consult your database administrator about configuration details for your specific installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14f8c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14f8c-119">See Also</span></span>  
 [<span data-ttu-id="14f8c-120">建立 Oracle E-business Suite 連線</span><span class="sxs-lookup"><span data-stu-id="14f8c-120">Create a connection to Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md)