---
title: ExportSettings 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa34dab1-c854-473e-a693-43ba45624e16
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab8c39ef6903affbd2a1446bbde18a56e1a7778c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245942"
---
# <a name="exportsettings-command"></a><span data-ttu-id="9d8f5-102">ExportSettings 命令</span><span class="sxs-lookup"><span data-stu-id="9d8f5-102">ExportSettings Command</span></span>
<span data-ttu-id="9d8f5-103">ExportSettings 指令碼可讓您將 BizTalk Server 組態資料庫中的 BizTalk Server 設定匯出至 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="9d8f5-103">The ExportSettings command nables you to export the BizTalk Server settings from a BizTalk Server configuration database to an XML file.</span></span> <span data-ttu-id="9d8f5-104">您可以再匯入另一個環境中的這些設定中所述[如何匯入 BizTalk 設定使用設定儀表板](../core/how-to-import-biztalk-settings-using-settings-dashboard.md)或[如何使用 BTSTask 匯入 BizTalk 設定](../core/how-to-import-biztalk-settings-using-btstask.md)。</span><span class="sxs-lookup"><span data-stu-id="9d8f5-104">You can then import these settings in another environment as described in [How to Import BizTalk Settings Using Settings Dashboard](../core/how-to-import-biztalk-settings-using-settings-dashboard.md) or [How to Import BizTalk Settings Using BTSTask](../core/how-to-import-biztalk-settings-using-btstask.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9d8f5-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="9d8f5-105">Prerequisites</span></span>  
 <span data-ttu-id="9d8f5-106">若要執行此作業，您必須以 BizTalk Server Administrators 群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="9d8f5-106">To perform this operation, you must be logged on as a member of the BizTalk Server Administrators group.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="9d8f5-107">使用方式</span><span class="sxs-lookup"><span data-stu-id="9d8f5-107">Usage</span></span>  
 `ExportSettings –Destination:value[-Server:value] [-Database:value]`  
  
## <a name="parameters"></a><span data-ttu-id="9d8f5-108">參數</span><span class="sxs-lookup"><span data-stu-id="9d8f5-108">Parameters</span></span>  
  
|<span data-ttu-id="9d8f5-109">**參數**</span><span class="sxs-lookup"><span data-stu-id="9d8f5-109">**Parameter**</span></span>|<span data-ttu-id="9d8f5-110">Required</span><span class="sxs-lookup"><span data-stu-id="9d8f5-110">Required</span></span>|<span data-ttu-id="9d8f5-111">值</span><span class="sxs-lookup"><span data-stu-id="9d8f5-111">Value</span></span>|  
|-------------------|--------------|-----------|  
|<span data-ttu-id="9d8f5-112">**目的端**</span><span class="sxs-lookup"><span data-stu-id="9d8f5-112">**-Destination**</span></span>|<span data-ttu-id="9d8f5-113">是</span><span class="sxs-lookup"><span data-stu-id="9d8f5-113">Yes</span></span>|<span data-ttu-id="9d8f5-114">要寫入之 XML 檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="9d8f5-114">Path and file name of the XML file to write.</span></span>|  
|<span data-ttu-id="9d8f5-115">**伺服器**</span><span class="sxs-lookup"><span data-stu-id="9d8f5-115">**-Server**</span></span>|<span data-ttu-id="9d8f5-116">選擇性</span><span class="sxs-lookup"><span data-stu-id="9d8f5-116">Optional</span></span>|<span data-ttu-id="9d8f5-117">裝載 BizTalk 組態資料庫的 SQL 伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="9d8f5-117">The name of SQL Server hosting the BizTalk configuration database.</span></span>|  
|<span data-ttu-id="9d8f5-118">**資料庫**</span><span class="sxs-lookup"><span data-stu-id="9d8f5-118">**-Database**</span></span>|<span data-ttu-id="9d8f5-119">選擇性</span><span class="sxs-lookup"><span data-stu-id="9d8f5-119">Optional</span></span>|<span data-ttu-id="9d8f5-120">BizTalk 組態資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="9d8f5-120">The name of the BizTalk configuration database.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="9d8f5-121">範例</span><span class="sxs-lookup"><span data-stu-id="9d8f5-121">Sample</span></span>  
 `BTSTask ExportSettings /Destination:MyFile.xml /Server:MyServer /Database:MyMgmtDb`  
  
## <a name="remarks"></a><span data-ttu-id="9d8f5-122">備註</span><span class="sxs-lookup"><span data-stu-id="9d8f5-122">Remarks</span></span>  
 <span data-ttu-id="9d8f5-123">參數不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="9d8f5-123">Parameters are not case-sensitive.</span></span> <span data-ttu-id="9d8f5-124">您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。</span><span class="sxs-lookup"><span data-stu-id="9d8f5-124">You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d8f5-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d8f5-125">See Also</span></span>  
 [<span data-ttu-id="9d8f5-126">BTSTask 命令列參考</span><span class="sxs-lookup"><span data-stu-id="9d8f5-126">BTSTask Command-Line Reference</span></span>](../core/btstask-command-line-reference.md)