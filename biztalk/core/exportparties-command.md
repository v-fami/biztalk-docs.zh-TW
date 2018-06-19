---
title: ExportParties 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b421c8ed-d505-48ba-9d1d-8519c9d51750
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ca525872ccc1cd941673189c4ac176fc4631f22
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245814"
---
# <a name="exportparties-command"></a><span data-ttu-id="e1ec7-102">ExportParties 命令</span><span class="sxs-lookup"><span data-stu-id="e1ec7-102">ExportParties Command</span></span>
<span data-ttu-id="e1ec7-103">將所有的合作對象和協議匯出為 XML 繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="e1ec7-103">Exports all the parties and agreements to an XML bindings file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1ec7-104">這個命令是新開頭 **[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** ，以及所有較新版本。</span><span class="sxs-lookup"><span data-stu-id="e1ec7-104">This command is new starting with **[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, and any newer versions.</span></span>

## <a name="usage"></a><span data-ttu-id="e1ec7-105">使用方式</span><span class="sxs-lookup"><span data-stu-id="e1ec7-105">Usage</span></span>
  <span data-ttu-id="e1ec7-106">**BTSTask ExportParties-目的地**:*值*[**-伺服器**:*值*] [**-資料庫**:*值*]</span><span class="sxs-lookup"><span data-stu-id="e1ec7-106">**BTSTask ExportParties -Destination**:*value* [**-Server**:*value*] [**-Database**:*value*]</span></span>
  
## <a name="parameters"></a><span data-ttu-id="e1ec7-107">參數</span><span class="sxs-lookup"><span data-stu-id="e1ec7-107">Parameters</span></span>

|<span data-ttu-id="e1ec7-108">參數</span><span class="sxs-lookup"><span data-stu-id="e1ec7-108">Parameter</span></span>|<span data-ttu-id="e1ec7-109">Required</span><span class="sxs-lookup"><span data-stu-id="e1ec7-109">Required</span></span>|<span data-ttu-id="e1ec7-110">值</span><span class="sxs-lookup"><span data-stu-id="e1ec7-110">Value</span></span>|  
|---|---|---|  
| <span data-ttu-id="e1ec7-111">**目的端**</span><span class="sxs-lookup"><span data-stu-id="e1ec7-111">**-Destination**</span></span> | <span data-ttu-id="e1ec7-112">Required</span><span class="sxs-lookup"><span data-stu-id="e1ec7-112">Required</span></span> | <span data-ttu-id="e1ec7-113">要寫入的 XML 繫結檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="e1ec7-113">Path and file name of the XML binding file to write.</span></span> |
| <span data-ttu-id="e1ec7-114">**伺服器**</span><span class="sxs-lookup"><span data-stu-id="e1ec7-114">**-Server**</span></span> | <span data-ttu-id="e1ec7-115">選擇性</span><span class="sxs-lookup"><span data-stu-id="e1ec7-115">Optional</span></span> | <span data-ttu-id="e1ec7-116">裝載 BizTalk 組態資料庫的 SQL server 名稱。</span><span class="sxs-lookup"><span data-stu-id="e1ec7-116">The name of SQL server hosting the BizTalk configuration database.</span></span> |
| <span data-ttu-id="e1ec7-117">**資料庫**</span><span class="sxs-lookup"><span data-stu-id="e1ec7-117">**-Database**</span></span> | <span data-ttu-id="e1ec7-118">選擇性</span><span class="sxs-lookup"><span data-stu-id="e1ec7-118">Optional</span></span> | <span data-ttu-id="e1ec7-119">BizTalk 組態資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="e1ec7-119">The name of the BizTalk configuration database.</span></span>|

## <a name="sample"></a><span data-ttu-id="e1ec7-120">範例</span><span class="sxs-lookup"><span data-stu-id="e1ec7-120">Sample</span></span>
  `ExportParties  -Destination:"C:\Temp\MyParties.Xml"` 

## <a name="remarks"></a><span data-ttu-id="e1ec7-121">備註</span><span class="sxs-lookup"><span data-stu-id="e1ec7-121">Remarks</span></span>
  <span data-ttu-id="e1ec7-122">匯出合作對象、 合約和 EDI 後援設定。</span><span class="sxs-lookup"><span data-stu-id="e1ec7-122">Only parties, agreements, and EDI fallback settings are exported.</span></span> <span data-ttu-id="e1ec7-123">沒有應用程式的成品都會匯出。</span><span class="sxs-lookup"><span data-stu-id="e1ec7-123">No application artifacts are exported.</span></span>
