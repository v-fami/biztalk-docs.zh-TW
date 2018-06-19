---
title: EncryptionCert （SendPort 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- EncryptionCert node [binding file]
ms.assetid: 83dff67e-1b3c-4c3d-91a2-d826a498635f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd51f4b339c5bdd228c692fffd7e6c487bb8c0ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240710"
---
# <a name="encryptioncert-sendport-node"></a><span data-ttu-id="08f16-102">EncryptionCert (SendPort 節點)</span><span class="sxs-lookup"><span data-stu-id="08f16-102">EncryptionCert (SendPort Node)</span></span>
<span data-ttu-id="08f16-103">繫結檔案的 SendPort 節點的 EncryptionCert 節點中，包含搭配隨同繫結檔案匯出之傳送埠所使用的加密憑證的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="08f16-103">The EncryptionCert node of the SendPort node of a binding file contains information about the encryption certificate used with a send port that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-encryptioncert-node"></a><span data-ttu-id="08f16-104">EncryptionCert 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="08f16-104">Nodes in the EncryptionCert node</span></span>  
 <span data-ttu-id="08f16-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="08f16-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="08f16-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="08f16-106">**Name**</span></span>|<span data-ttu-id="08f16-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="08f16-107">**Node Type**</span></span>|<span data-ttu-id="08f16-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="08f16-108">**Data Type**</span></span>|<span data-ttu-id="08f16-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="08f16-109">**Description**</span></span>|<span data-ttu-id="08f16-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="08f16-110">**Restrictions**</span></span>|<span data-ttu-id="08f16-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="08f16-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="08f16-112">LongName</span><span class="sxs-lookup"><span data-stu-id="08f16-112">LongName</span></span>|<span data-ttu-id="08f16-113">Attribute</span><span class="sxs-lookup"><span data-stu-id="08f16-113">Attribute</span></span>|<span data-ttu-id="08f16-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="08f16-114">xs:string</span></span>|<span data-ttu-id="08f16-115">指定憑證的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="08f16-115">Specifies the long name of the certificate.</span></span>|<span data-ttu-id="08f16-116">不需要</span><span class="sxs-lookup"><span data-stu-id="08f16-116">Not required</span></span>|<span data-ttu-id="08f16-117">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="08f16-117">Default value: empty</span></span>|  
|<span data-ttu-id="08f16-118">ShortName</span><span class="sxs-lookup"><span data-stu-id="08f16-118">ShortName</span></span>|<span data-ttu-id="08f16-119">Attribute</span><span class="sxs-lookup"><span data-stu-id="08f16-119">Attribute</span></span>|<span data-ttu-id="08f16-120">xs:string</span><span class="sxs-lookup"><span data-stu-id="08f16-120">xs:string</span></span>|<span data-ttu-id="08f16-121">指定憑證的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="08f16-121">Specifies the short name of the certificate.</span></span>|<span data-ttu-id="08f16-122">不需要</span><span class="sxs-lookup"><span data-stu-id="08f16-122">Not required</span></span>|<span data-ttu-id="08f16-123">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="08f16-123">Default value: empty</span></span>|  
|<span data-ttu-id="08f16-124">UsageType</span><span class="sxs-lookup"><span data-stu-id="08f16-124">UsageType</span></span>|<span data-ttu-id="08f16-125">Attribute</span><span class="sxs-lookup"><span data-stu-id="08f16-125">Attribute</span></span>|<span data-ttu-id="08f16-126">CertUsageType (SimpleType)</span><span class="sxs-lookup"><span data-stu-id="08f16-126">CertUsageType (SimpleType)</span></span>|<span data-ttu-id="08f16-127">指定這個憑證的預定使用方式</span><span class="sxs-lookup"><span data-stu-id="08f16-127">Specifies the intended usage of this certificate</span></span>|<span data-ttu-id="08f16-128">Required</span><span class="sxs-lookup"><span data-stu-id="08f16-128">Required</span></span>|<span data-ttu-id="08f16-129">預設值：無</span><span class="sxs-lookup"><span data-stu-id="08f16-129">Default value: none</span></span><br /><br /> <span data-ttu-id="08f16-130">可能的值包括用於[Microsoft.BizTalk.ExplorerOM.CertUsageType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.certusagetype.aspx)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="08f16-130">Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.CertUsageType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.certusagetype.aspx) enumeration.</span></span>|  
|<span data-ttu-id="08f16-131">ThumbPrint</span><span class="sxs-lookup"><span data-stu-id="08f16-131">ThumbPrint</span></span>|<span data-ttu-id="08f16-132">Attribute</span><span class="sxs-lookup"><span data-stu-id="08f16-132">Attribute</span></span>|<span data-ttu-id="08f16-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="08f16-133">xs:string</span></span>|<span data-ttu-id="08f16-134">指定憑證的指紋 (或唯一識別碼)</span><span class="sxs-lookup"><span data-stu-id="08f16-134">Specifies the thumbprint, or unique ID, of the certificate.</span></span>|<span data-ttu-id="08f16-135">不需要</span><span class="sxs-lookup"><span data-stu-id="08f16-135">Not required</span></span>|<span data-ttu-id="08f16-136">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="08f16-136">Default value: empty</span></span>|