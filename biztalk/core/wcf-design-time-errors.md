---
title: WCF 設計階段錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1327906a-6524-4937-830c-844d5fc81dc6
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 945093f62c9d0d45fd359dbfabe8a0e495850f6d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288782"
---
# <a name="wcf-design-time--errors"></a><span data-ttu-id="9008d-102">WCF 設計階段錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-102">WCF Design-Time  Errors</span></span>
<span data-ttu-id="9008d-103">本節包含診斷及解決 WCF 設計階段組態錯誤的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="9008d-103">This section contains detailed information for diagnosing and resolving WCF design-time configuration errors.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9008d-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="9008d-104">In This Section</span></span>  
  
-   [<span data-ttu-id="9008d-105">動作的錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-105">Action Errors</span></span>](../core/action-errors.md)  
  
-   [<span data-ttu-id="9008d-106">解決錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-106">Address Errors</span></span>](../core/address-errors.md)  
  
-   [<span data-ttu-id="9008d-107">應用程式錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-107">Application Errors</span></span>](../core/application-errors.md)  
  
-   [<span data-ttu-id="9008d-108">組件錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-108">Assembly Errors</span></span>](../core/assembly-errors.md)  
  
-   [<span data-ttu-id="9008d-109">繫結錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-109">Binding Errors</span></span>](../core/binding-errors.md)  
  
-   [<span data-ttu-id="9008d-110">憑證錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-110">Certificate Errors</span></span>](../core/certificate-errors.md)  
  
-   [<span data-ttu-id="9008d-111">通訊模式錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-111">Communication Pattern Errors</span></span>](../core/communication-pattern-errors.md)  
  
-   [<span data-ttu-id="9008d-112">錯誤處理錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-112">Error Handling Errors</span></span>](../core/error-handling-errors.md)  
  
-   [<span data-ttu-id="9008d-113">識別錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-113">Identity Errors</span></span>](../core/identity-errors.md)  
  
-   [<span data-ttu-id="9008d-114">匯入和匯出錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-114">Import and Export Errors</span></span>](../core/import-and-export-errors.md)  
  
-   [<span data-ttu-id="9008d-115">中繼資料錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-115">Metadata Errors</span></span>](../core/metadata-errors.md)  
  
-   [<span data-ttu-id="9008d-116">名稱錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-116">Name Errors</span></span>](../core/name-errors.md)  
  
-   [<span data-ttu-id="9008d-117">連接埠組態錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-117">Port Configuration Errors</span></span>](../core/port-configuration-errors.md)  
  
-   [<span data-ttu-id="9008d-118">內容錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-118">Properties Errors</span></span>](../core/properties-errors.md)  
  
-   [<span data-ttu-id="9008d-119">收到的錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-119">Receive Errors</span></span>](../core/receive-errors.md)  
  
-   [<span data-ttu-id="9008d-120">登錄錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-120">Registry Errors</span></span>](../core/registry-errors.md)  
  
-   [<span data-ttu-id="9008d-121">配置錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-121">Scheme Errors</span></span>](../core/scheme-errors.md)  
  
-   [<span data-ttu-id="9008d-122">傳送錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-122">Send Errors</span></span>](../core/send-errors.md)  
  
-   [<span data-ttu-id="9008d-123">範本錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-123">Template Errors</span></span>](../core/template-errors.md)  
  
-   [<span data-ttu-id="9008d-124">逾時錯誤</span><span class="sxs-lookup"><span data-stu-id="9008d-124">Timeout Errors</span></span>](../core/timeout-errors.md)