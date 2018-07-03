---
title: ImportParties 命令 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87d43e2c-401c-4450-ad9b-2528086b99e4
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6c25b913b6479b857fb7cee4aec10e6984f2195
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998535"
---
# <a name="importparties-command"></a><span data-ttu-id="75393-102">ImportParties 命令</span><span class="sxs-lookup"><span data-stu-id="75393-102">ImportParties Command</span></span>
<span data-ttu-id="75393-103">企業對企業的合作對象和協議從檔案匯入來源 XML 繫結在組態資料庫中，但不匯入的任何應用程式成品。</span><span class="sxs-lookup"><span data-stu-id="75393-103">Imports the business-to-business parties and agreements from a source XML binding file in the configuration database, without importing any of the application artifacts.</span></span> <span data-ttu-id="75393-104">如需詳細資訊，請參閱 <<c0>  **備註**本主題中。</span><span class="sxs-lookup"><span data-stu-id="75393-104">For more information, see **Remarks** in this topic.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="75393-105">此命令的新開頭**[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**，以及所有較新版本。</span><span class="sxs-lookup"><span data-stu-id="75393-105">This command is new starting with **[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, and any newer versions.</span></span>
> 
> [!NOTE]
>  <span data-ttu-id="75393-106">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中產生的繫結檔案均未指定應用程式。</span><span class="sxs-lookup"><span data-stu-id="75393-106">Binding files generated in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] do not have an application specified.</span></span> <span data-ttu-id="75393-107">這些檔案將匯入到預設的應用程式。</span><span class="sxs-lookup"><span data-stu-id="75393-107">They are imported into the default application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="75393-108">使用方式</span><span class="sxs-lookup"><span data-stu-id="75393-108">Usage</span></span>  
  <span data-ttu-id="75393-109">**BTSTask ImportParties-來源**:*值*[**-ExcludeEdiFallbackSettings**] [**-Server**:*值*] [**-資料庫**:*值*]</span><span class="sxs-lookup"><span data-stu-id="75393-109">**BTSTask ImportParties -Source**:*value* [**-ExcludeEdiFallbackSettings**] [**-Server**:*value*] [**-Database**:*value*]</span></span>
  
## <a name="parameters"></a><span data-ttu-id="75393-110">參數</span><span class="sxs-lookup"><span data-stu-id="75393-110">Parameters</span></span>  
  
|<span data-ttu-id="75393-111">參數</span><span class="sxs-lookup"><span data-stu-id="75393-111">Parameter</span></span>|<span data-ttu-id="75393-112">必要項</span><span class="sxs-lookup"><span data-stu-id="75393-112">Required</span></span>|<span data-ttu-id="75393-113">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="75393-113">Value</span></span>|  
|---|---|---|  
|<span data-ttu-id="75393-114">**原始碼**</span><span class="sxs-lookup"><span data-stu-id="75393-114">**-Source**</span></span> | <span data-ttu-id="75393-115">必要項</span><span class="sxs-lookup"><span data-stu-id="75393-115">Required</span></span> | <span data-ttu-id="75393-116">要讀取之 XML 繫結檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="75393-116">The path and file name of the XML binding file to read.</span></span>|
|<span data-ttu-id="75393-117">**-ExcludeEdiFallbackSettings**</span><span class="sxs-lookup"><span data-stu-id="75393-117">**-ExcludeEdiFallbackSettings**</span></span> | <span data-ttu-id="75393-118">選擇性</span><span class="sxs-lookup"><span data-stu-id="75393-118">Optional</span></span> | <span data-ttu-id="75393-119">如果指定，將會排除 edi 後援 （x12 和 edifact） 設定繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="75393-119">If specified, it excludes edi fallback (x12 and edifact) settings from the binding file.</span></span>  |
| <span data-ttu-id="75393-120">**伺服器**</span><span class="sxs-lookup"><span data-stu-id="75393-120">**-Server**</span></span> | <span data-ttu-id="75393-121">選擇性</span><span class="sxs-lookup"><span data-stu-id="75393-121">Optional</span></span> | <span data-ttu-id="75393-122">裝載 BizTalk 組態資料庫的 SQL server 名稱。</span><span class="sxs-lookup"><span data-stu-id="75393-122">The name of SQL server hosting the BizTalk configuration database.</span></span> |
| <span data-ttu-id="75393-123">**-資料庫**</span><span class="sxs-lookup"><span data-stu-id="75393-123">**-Database**</span></span> | <span data-ttu-id="75393-124">選擇性</span><span class="sxs-lookup"><span data-stu-id="75393-124">Optional</span></span> | <span data-ttu-id="75393-125">BizTalk 組態資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="75393-125">The name of the BizTalk configuration database.</span></span> |

## <a name="sample"></a><span data-ttu-id="75393-126">範例</span><span class="sxs-lookup"><span data-stu-id="75393-126">Sample</span></span>
  `BTSTask ImportParties  -Source:"C:\Temp\MyParties.Xml" -ExcludeEdiFallbackSettings`

## <a name="remarks"></a><span data-ttu-id="75393-127">備註</span><span class="sxs-lookup"><span data-stu-id="75393-127">Remarks</span></span>
<span data-ttu-id="75393-128">如果繫結檔案中也有應用程式成品，然後它們不會匯入。</span><span class="sxs-lookup"><span data-stu-id="75393-128">If the binding file also has application artifacts, then they are not imported.</span></span> <span data-ttu-id="75393-129">只有合作對象與合約匯入。</span><span class="sxs-lookup"><span data-stu-id="75393-129">Only parties and agreements are imported.</span></span>