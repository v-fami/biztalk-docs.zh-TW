---
title: "ImportSettings 命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 587f7e1f-9cf7-4e7b-90cd-11a266f474dc
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c609634422f8c8b5f2c1a96691fe4eda708e5c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="importsettings-command"></a><span data-ttu-id="3dc80-102">ImportSettings 命令</span><span class="sxs-lookup"><span data-stu-id="3dc80-102">ImportSettings Command</span></span>
<span data-ttu-id="3dc80-103">從來源 XML 檔案將 BizTalk 群組、主控件或主控件執行個體設定匯入組態資料庫。</span><span class="sxs-lookup"><span data-stu-id="3dc80-103">Imports the BizTalk group, host, or host instance settings from a source XML file to the configuration database.</span></span> <span data-ttu-id="3dc80-104">設定在匯入對應的 XML 檔案中後會進行對應。</span><span class="sxs-lookup"><span data-stu-id="3dc80-104">The settings are mapped as they are in the mapping XML file.</span></span> <span data-ttu-id="3dc80-105">這些設定可能是已匯出中所述[匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)或[匯入或匯出 BizTalk 設定使用 BTSTask](how-to-import-biztalk-settings-using-btstask.md)。</span><span class="sxs-lookup"><span data-stu-id="3dc80-105">These settings may have been exported as described in [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md) or [Import or export BizTalk Settings Using BTSTask](how-to-import-biztalk-settings-using-btstask.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3dc80-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="3dc80-106">Prerequisites</span></span>  
 <span data-ttu-id="3dc80-107">若要執行這項作業，您必須為 BizTalk Server 系統管理員群組的成員登入。</span><span class="sxs-lookup"><span data-stu-id="3dc80-107">To perform this operation, you must be signed in as a member of the BizTalk Server Administrators group.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="3dc80-108">使用方式</span><span class="sxs-lookup"><span data-stu-id="3dc80-108">Usage</span></span>  
 `ImportSettings –Source:value –Map: value [-Server:value] [-Database:value]`  
  
## <a name="parameters"></a><span data-ttu-id="3dc80-109">參數</span><span class="sxs-lookup"><span data-stu-id="3dc80-109">Parameters</span></span>  
  
|<span data-ttu-id="3dc80-110">**參數**</span><span class="sxs-lookup"><span data-stu-id="3dc80-110">**Parameter**</span></span>|<span data-ttu-id="3dc80-111">Required</span><span class="sxs-lookup"><span data-stu-id="3dc80-111">Required</span></span>|<span data-ttu-id="3dc80-112">值</span><span class="sxs-lookup"><span data-stu-id="3dc80-112">Value</span></span>|  
|-------------------|--------------|-----------|  
|<span data-ttu-id="3dc80-113">**原始碼**</span><span class="sxs-lookup"><span data-stu-id="3dc80-113">**-Source**</span></span>|<span data-ttu-id="3dc80-114">是</span><span class="sxs-lookup"><span data-stu-id="3dc80-114">Yes</span></span>|<span data-ttu-id="3dc80-115">匯出的設定 XML 檔案的路徑與檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="3dc80-115">Path and file name of the exported settings XML file.</span></span>|  
|<span data-ttu-id="3dc80-116">**-對應**</span><span class="sxs-lookup"><span data-stu-id="3dc80-116">**-Map**</span></span>|<span data-ttu-id="3dc80-117">是</span><span class="sxs-lookup"><span data-stu-id="3dc80-117">Yes</span></span>|<span data-ttu-id="3dc80-118">對應的設定 XML 檔案的路徑與檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="3dc80-118">Path and file name of the mapping XML file.</span></span>|  
|<span data-ttu-id="3dc80-119">**伺服器**</span><span class="sxs-lookup"><span data-stu-id="3dc80-119">**-Server**</span></span>|<span data-ttu-id="3dc80-120">選擇性</span><span class="sxs-lookup"><span data-stu-id="3dc80-120">Optional</span></span>|<span data-ttu-id="3dc80-121">裝載 BizTalk 組態資料庫的 SQL Server 電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="3dc80-121">The name of SQL Server computer hosting the BizTalk configuration database.</span></span>|  
|<span data-ttu-id="3dc80-122">**資料庫**</span><span class="sxs-lookup"><span data-stu-id="3dc80-122">**-Database**</span></span>|<span data-ttu-id="3dc80-123">選擇性</span><span class="sxs-lookup"><span data-stu-id="3dc80-123">Optional</span></span>|<span data-ttu-id="3dc80-124">BizTalk 組態資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="3dc80-124">The name of the BizTalk configuration database.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="3dc80-125">範例</span><span class="sxs-lookup"><span data-stu-id="3dc80-125">Sample</span></span>  
 `BTSTask ImportSettings /Source:”C:\My Folder>\ExportedSettings.xml” /Map:Mappings.xml /Server:MyServer /Database:MyMgmtDb`  
  
## <a name="remarks"></a><span data-ttu-id="3dc80-126">備註</span><span class="sxs-lookup"><span data-stu-id="3dc80-126">Remarks</span></span>  
 <span data-ttu-id="3dc80-127">參數不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3dc80-127">Parameters are not case-sensitive.</span></span> <span data-ttu-id="3dc80-128">您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。</span><span class="sxs-lookup"><span data-stu-id="3dc80-128">You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dc80-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3dc80-129">See Also</span></span>  
 [<span data-ttu-id="3dc80-130">BTSTask 命令列參考</span><span class="sxs-lookup"><span data-stu-id="3dc80-130">BTSTask Command-Line Reference</span></span>](../core/btstask-command-line-reference.md)