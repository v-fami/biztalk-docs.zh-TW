---
title: "EncryptionCert （ReceiveLocation 節點） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: EncryptionCert node [binding file]
ms.assetid: 04dc4021-8cd9-45e7-8339-8f22e29f4be6
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec4d0ff769c7a8ca297800f427c4ebbae48a8640
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="encryptioncert-receivelocation-node"></a><span data-ttu-id="857e4-102">EncryptionCert (ReceiveLocation 節點)</span><span class="sxs-lookup"><span data-stu-id="857e4-102">EncryptionCert (ReceiveLocation Node)</span></span>
<span data-ttu-id="857e4-103">繫結檔案的 ReceiveLocation 節點的 EncryptionCert 節點中，包含隨同繫結檔案匯出之接收位置所使用的加密憑證相關資訊。</span><span class="sxs-lookup"><span data-stu-id="857e4-103">The EncryptionCert node of the ReceiveLocation node of a binding file contains information about the encryption certificate used with a receive location that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-encryptioncert-node"></a><span data-ttu-id="857e4-104">EncryptionCert 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="857e4-104">Nodes in the EncryptionCert node</span></span>  
 <span data-ttu-id="857e4-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="857e4-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="857e4-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="857e4-106">**Name**</span></span>|<span data-ttu-id="857e4-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="857e4-107">**Node Type**</span></span>|<span data-ttu-id="857e4-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="857e4-108">**Data Type**</span></span>|<span data-ttu-id="857e4-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="857e4-109">**Description**</span></span>|<span data-ttu-id="857e4-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="857e4-110">**Restrictions**</span></span>|<span data-ttu-id="857e4-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="857e4-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="857e4-112">LongName</span><span class="sxs-lookup"><span data-stu-id="857e4-112">LongName</span></span>|<span data-ttu-id="857e4-113">Attribute</span><span class="sxs-lookup"><span data-stu-id="857e4-113">Attribute</span></span>|<span data-ttu-id="857e4-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="857e4-114">xs:string</span></span>|<span data-ttu-id="857e4-115">指定憑證的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="857e4-115">Specifies the long name of the certificate.</span></span>|<span data-ttu-id="857e4-116">不需要</span><span class="sxs-lookup"><span data-stu-id="857e4-116">Not required</span></span>|<span data-ttu-id="857e4-117">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="857e4-117">Default value: empty</span></span>|  
|<span data-ttu-id="857e4-118">ShortName</span><span class="sxs-lookup"><span data-stu-id="857e4-118">ShortName</span></span>|<span data-ttu-id="857e4-119">Attribute</span><span class="sxs-lookup"><span data-stu-id="857e4-119">Attribute</span></span>|<span data-ttu-id="857e4-120">xs:string</span><span class="sxs-lookup"><span data-stu-id="857e4-120">xs:string</span></span>|<span data-ttu-id="857e4-121">指定憑證的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="857e4-121">Specifies the short name of the certificate.</span></span>|<span data-ttu-id="857e4-122">不需要</span><span class="sxs-lookup"><span data-stu-id="857e4-122">Not required</span></span>|<span data-ttu-id="857e4-123">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="857e4-123">Default value: empty</span></span>|  
|<span data-ttu-id="857e4-124">UsageType</span><span class="sxs-lookup"><span data-stu-id="857e4-124">UsageType</span></span>|<span data-ttu-id="857e4-125">Attribute</span><span class="sxs-lookup"><span data-stu-id="857e4-125">Attribute</span></span>|<span data-ttu-id="857e4-126">CertUsageType (SimpleType)</span><span class="sxs-lookup"><span data-stu-id="857e4-126">CertUsageType (SimpleType)</span></span>|<span data-ttu-id="857e4-127">指定這個憑證的預定使用方式</span><span class="sxs-lookup"><span data-stu-id="857e4-127">Specifies the intended usage of this certificate</span></span>|<span data-ttu-id="857e4-128">Required</span><span class="sxs-lookup"><span data-stu-id="857e4-128">Required</span></span>|<span data-ttu-id="857e4-129">預設值：無</span><span class="sxs-lookup"><span data-stu-id="857e4-129">Default value: none</span></span><br /><br /> <span data-ttu-id="857e4-130">可能的值包括用於[Microsoft.BizTalk.ExplorerOM.CertUsageType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.certusagetype.aspx)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="857e4-130">Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.CertUsageType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.certusagetype.aspx) enumeration.</span></span>|  
|<span data-ttu-id="857e4-131">ThumbPrint</span><span class="sxs-lookup"><span data-stu-id="857e4-131">ThumbPrint</span></span>|<span data-ttu-id="857e4-132">Attribute</span><span class="sxs-lookup"><span data-stu-id="857e4-132">Attribute</span></span>|<span data-ttu-id="857e4-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="857e4-133">xs:string</span></span>|<span data-ttu-id="857e4-134">指定憑證的指紋 (或唯一識別碼)</span><span class="sxs-lookup"><span data-stu-id="857e4-134">Specifies the thumbprint, or unique ID, of the certificate.</span></span>|<span data-ttu-id="857e4-135">不需要</span><span class="sxs-lookup"><span data-stu-id="857e4-135">Not required</span></span>|<span data-ttu-id="857e4-136">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="857e4-136">Default value: empty</span></span>|