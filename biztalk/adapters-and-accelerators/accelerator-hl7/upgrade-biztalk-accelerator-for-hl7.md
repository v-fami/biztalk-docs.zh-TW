---
title: 升級 BizTalk Accelerator for HL7 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 91b6747f-e560-4cf8-99b5-af0d150599bf
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 245d59e54a39cb77a71fc546920542619a4aeb3f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977639"
---
# <a name="upgrade-biztalk-accelerator-for-hl7"></a><span data-ttu-id="f9013-102">升級 BizTalk Accelerator for HL7</span><span class="sxs-lookup"><span data-stu-id="f9013-102">Upgrade BizTalk Accelerator for HL7</span></span>
<span data-ttu-id="f9013-103">概觀[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]升級程序。</span><span class="sxs-lookup"><span data-stu-id="f9013-103">Overview of the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] upgrade process.</span></span> 

<a name="BKMK_BeforeUpgrade"></a>   
## <a name="before-you-upgrade"></a><span data-ttu-id="f9013-104">升級之前</span><span class="sxs-lookup"><span data-stu-id="f9013-104">Before you upgrade</span></span>  

- <span data-ttu-id="f9013-105">執行升級的使用者必須是 BizTalk 系統管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="f9013-105">The user running the upgrade must be a member of the BizTalk Administrators group.</span></span>  

- <span data-ttu-id="f9013-106">當您執行升級時，必須執行 SQL Server (MSSQLSERVER) 服務。</span><span class="sxs-lookup"><span data-stu-id="f9013-106">The SQL Server (MSSQLSERVER) service must be running when you perform an upgrade.</span></span>  

- <span data-ttu-id="f9013-107">請勿執行無訊息安裝來升級。</span><span class="sxs-lookup"><span data-stu-id="f9013-107">Do not run a silent installation to upgrade.</span></span>  

- <span data-ttu-id="f9013-108">當您升級時，安裝程式會移轉現有[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]較新版本的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="f9013-108">When you upgrade, the setup program migrates the existing [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] configuration information to the newer version.</span></span>  

- <span data-ttu-id="f9013-109">當您升級時，登錄機碼和資料庫會自動備份。</span><span class="sxs-lookup"><span data-stu-id="f9013-109">When you upgrade, the registry keys and databases are automatically backed up.</span></span>  

- <span data-ttu-id="f9013-110">中的檔案*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7 資料夾會更新。</span><span class="sxs-lookup"><span data-stu-id="f9013-110">The files in the *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7 folder are updated.</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="f9013-111">升級不會建立新的資料夾，針對已升級的檔案，也不會變更現有資料夾的名稱。</span><span class="sxs-lookup"><span data-stu-id="f9013-111">The upgrade does not create a new folder for the upgraded files, nor does it change the name of the existing folder.</span></span>  

<a name="BKMK_UpgradePaths"></a>   
## <a name="supported-upgrade-paths"></a><span data-ttu-id="f9013-112">支援的升級路徑</span><span class="sxs-lookup"><span data-stu-id="f9013-112">Supported Upgrade Paths</span></span>  
 <span data-ttu-id="f9013-113">下表列出支援[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可以升級的版本。</span><span class="sxs-lookup"><span data-stu-id="f9013-113">The following table lists the supported [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] versions that can be upgraded.</span></span> <span data-ttu-id="f9013-114">「 是 」 表示[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]版本可以升級。</span><span class="sxs-lookup"><span data-stu-id="f9013-114">“Yes” means the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] version can be upgraded.</span></span> <span data-ttu-id="f9013-115">「 否 」 表示[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]版本無法升級。</span><span class="sxs-lookup"><span data-stu-id="f9013-115">“No” means the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] version cannot be upgraded.</span></span> <span data-ttu-id="f9013-116">如果[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]版本中沒有列出，該版本無法升級。</span><span class="sxs-lookup"><span data-stu-id="f9013-116">If the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] version is not listed, that version cannot be upgraded.</span></span>  


|                                                                                              | [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)] | [!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)] | <span data-ttu-id="f9013-117">BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="f9013-117">BizTalk Server 2013</span></span> |
|----------------------------------------------------------------------------------------------|------------------------------------------------------|-------------------------------------------------------|---------------------|
| [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="f9013-118"> 2013</span><span class="sxs-lookup"><span data-stu-id="f9013-118"> 2013</span></span> |                         <span data-ttu-id="f9013-119">是</span><span class="sxs-lookup"><span data-stu-id="f9013-119">Yes</span></span>                          |                          <span data-ttu-id="f9013-120">是</span><span class="sxs-lookup"><span data-stu-id="f9013-120">Yes</span></span>                          |         <span data-ttu-id="f9013-121">否</span><span class="sxs-lookup"><span data-stu-id="f9013-121">No</span></span>          |
| [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="f9013-122"> 2010</span><span class="sxs-lookup"><span data-stu-id="f9013-122"> 2010</span></span> |                          <span data-ttu-id="f9013-123">否</span><span class="sxs-lookup"><span data-stu-id="f9013-123">No</span></span>                          |                          <span data-ttu-id="f9013-124">是</span><span class="sxs-lookup"><span data-stu-id="f9013-124">Yes</span></span>                          |         <span data-ttu-id="f9013-125">是</span><span class="sxs-lookup"><span data-stu-id="f9013-125">Yes</span></span>         |

<a name="BKMK_UpgradeSteps"></a>   
## <a name="upgrade-steps"></a><span data-ttu-id="f9013-126">升級步驟</span><span class="sxs-lookup"><span data-stu-id="f9013-126">Upgrade Steps</span></span>  

1. <span data-ttu-id="f9013-127">升級[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f9013-127">Upgrade the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>   

2. <span data-ttu-id="f9013-128">備份[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]資料庫和您 HL7 訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="f9013-128">Back up the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] databases and your HL7 message schemas.</span></span>  

3. <span data-ttu-id="f9013-129">備份下的任何檔案 ***\<磁碟機\>*:\Program Files\Microsoft BizTalk Accelerator for HL7**已變更的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f9013-129">Back up any files under the ***\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for HL7** folder that you have changed.</span></span> <span data-ttu-id="f9013-130">例如，備份在 SDK 中的檔案。</span><span class="sxs-lookup"><span data-stu-id="f9013-130">For example, back up files in the SDK.</span></span>  

4. <span data-ttu-id="f9013-131">安裝適當的更新，您的版本[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="f9013-131">Install the appropriate update for your version of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]:</span></span>  

   -   <span data-ttu-id="f9013-132">如果從 BTAHL7 2010 升級，安裝**HL72010Patch.msp**。</span><span class="sxs-lookup"><span data-stu-id="f9013-132">If upgrading from BTAHL7 2010, install **HL72010Patch.msp**.</span></span>  

   -   <span data-ttu-id="f9013-133">如果從 BTAHL7 2013 升級，安裝**HL72013Patch.msp**。</span><span class="sxs-lookup"><span data-stu-id="f9013-133">If upgrading from BTAHL7 2013, install **HL72013Patch.msp**.</span></span>  


5. <span data-ttu-id="f9013-134">執行[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]安裝程式。</span><span class="sxs-lookup"><span data-stu-id="f9013-134">Run the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] setup.</span></span> <span data-ttu-id="f9013-135">請參閱[安裝 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)。</span><span class="sxs-lookup"><span data-stu-id="f9013-135">See [Install BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).</span></span>  

6. <span data-ttu-id="f9013-136">部署新的 BTAHL7V2*x*常見專案。</span><span class="sxs-lookup"><span data-stu-id="f9013-136">Deploy the new BTAHL7V2*x*Common project.</span></span>  

7. <span data-ttu-id="f9013-137">重新部署所有其他組件。</span><span class="sxs-lookup"><span data-stu-id="f9013-137">Redeploy all other assemblies.</span></span>  

8. <span data-ttu-id="f9013-138">重新建置參考一或多個 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 組件的任何專案或組件。</span><span class="sxs-lookup"><span data-stu-id="f9013-138">Rebuild any projects or assemblies that have a reference to one or more of the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] assemblies.</span></span> <span data-ttu-id="f9013-139">使用**BTSTask.exe**中\<*磁碟機*\>: \Program Files\Microsoft BizTalk Server\<版本\>，請手動重新部署這些專案。</span><span class="sxs-lookup"><span data-stu-id="f9013-139">Using **BTSTask.exe** in \<*drive*\>:\Program Files\Microsoft BizTalk Server \<version\>, manually redeploy these projects.</span></span>  

9. <span data-ttu-id="f9013-140">重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="f9013-140">Restart the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] service.</span></span>  

<a name="BKMK_UpgradeMulti"></a>   
## <a name="upgrading-in-a-multi-server-environment"></a><span data-ttu-id="f9013-141">多伺服器環境中升級</span><span class="sxs-lookup"><span data-stu-id="f9013-141">Upgrading in a Multi-server Environment</span></span>  
 <span data-ttu-id="f9013-142">在多伺服器[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]環境，則升級所有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，然後再升級[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]所有伺服器上。</span><span class="sxs-lookup"><span data-stu-id="f9013-142">In a multi-server [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] environment, upgrade all [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]s, and then upgrade the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] on all servers.</span></span> <span data-ttu-id="f9013-143">請依下列順序移轉您的伺服器：</span><span class="sxs-lookup"><span data-stu-id="f9013-143">Migrate your servers in the following order:</span></span>  

-   <span data-ttu-id="f9013-144">裝載 BizTalk 群組的伺服器</span><span class="sxs-lookup"><span data-stu-id="f9013-144">The server hosting the BizTalk Group</span></span>  

-   <span data-ttu-id="f9013-145">每個處理節點</span><span class="sxs-lookup"><span data-stu-id="f9013-145">Each processing node</span></span>  

-   <span data-ttu-id="f9013-146">BAM 入口網站伺服器</span><span class="sxs-lookup"><span data-stu-id="f9013-146">The BAM portal server</span></span>  

## <a name="see-also"></a><span data-ttu-id="f9013-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9013-147">See Also</span></span>  
 [<span data-ttu-id="f9013-148">安裝 BizTalk Accelerator for HL7</span><span class="sxs-lookup"><span data-stu-id="f9013-148">Install BizTalk Accelerator for HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)