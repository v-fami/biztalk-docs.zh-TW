---
title: "POP3 配接器屬性結構描述和屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, POP3 adapters
- Subject properties [POP3 adapters]
- Date properties [POP3 adapters]
- From properties [POP3 adapters]
- To properties [POP3 adapters]
- POP3 adapters, properties
- configuring [POP3 adapters], schemas
- configuring [POP3 adapters], properties
- CC properties [POP3 adapters]
- Headers properties [POP3 adapters]
- ReplyTo properties [POP3 adapters]
- DispositionNotificationTo properties [POP3 adapters]
ms.assetid: 7a10ae1f-dbcf-4c05-9a50-2503895960f9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b976aba7161272ebdc65da2b5bcd2067c8cd3a5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="pop3-adapter-property-schema-and-properties"></a><span data-ttu-id="caea4-102">POP3 配接器屬性結構描述和屬性</span><span class="sxs-lookup"><span data-stu-id="caea4-102">POP3 Adapter Property Schema and Properties</span></span>
<span data-ttu-id="caea4-103">下表列出 POP3 配接器屬性結構描述中的屬性。</span><span class="sxs-lookup"><span data-stu-id="caea4-103">The following table lists the properties in the POP3 adapter property schema.</span></span>  
  
 <span data-ttu-id="caea4-104">**命名空間：** http://schemas.microsoft.com/BizTalk/2003/pop3-properties</span><span class="sxs-lookup"><span data-stu-id="caea4-104">**Namespace:** http://schemas.microsoft.com/BizTalk/2003/pop3-properties</span></span>  
  
|<span data-ttu-id="caea4-105">**名稱**</span><span class="sxs-lookup"><span data-stu-id="caea4-105">**Name**</span></span>|<span data-ttu-id="caea4-106">**型別**</span><span class="sxs-lookup"><span data-stu-id="caea4-106">**Type**</span></span>|<span data-ttu-id="caea4-107">**說明**</span><span class="sxs-lookup"><span data-stu-id="caea4-107">**Description**</span></span>|  
|--------------|--------------|---------------------|  
|<span data-ttu-id="caea4-108">**主旨**</span><span class="sxs-lookup"><span data-stu-id="caea4-108">**Subject**</span></span>|<span data-ttu-id="caea4-109">xs:string</span><span class="sxs-lookup"><span data-stu-id="caea4-109">xs:string</span></span>|<span data-ttu-id="caea4-110">指定的內容放在**主旨**訊息標頭</span><span class="sxs-lookup"><span data-stu-id="caea4-110">Specifies the content placed on the **Subject** header for the message</span></span>|  
|<span data-ttu-id="caea4-111">**來源**</span><span class="sxs-lookup"><span data-stu-id="caea4-111">**From**</span></span>|<span data-ttu-id="caea4-112">xs:string</span><span class="sxs-lookup"><span data-stu-id="caea4-112">xs:string</span></span>|<span data-ttu-id="caea4-113">指定放在電子郵件地址**從**標頭欄位的電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="caea4-113">Specifies the e-mail address placed on the **From** header field of the e-mail message.</span></span>|  
|<span data-ttu-id="caea4-114">**若要**</span><span class="sxs-lookup"><span data-stu-id="caea4-114">**To**</span></span>|<span data-ttu-id="caea4-115">xs:string</span><span class="sxs-lookup"><span data-stu-id="caea4-115">xs:string</span></span>|<span data-ttu-id="caea4-116">指定的電子郵件地址或多個放**至**標頭欄位的電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="caea4-116">Specifies the e-mail address or addresses placed on the **To** header field of the e-mail message.</span></span>|  
|<span data-ttu-id="caea4-117">**ReplyTo**</span><span class="sxs-lookup"><span data-stu-id="caea4-117">**ReplyTo**</span></span>|<span data-ttu-id="caea4-118">xs:string</span><span class="sxs-lookup"><span data-stu-id="caea4-118">xs:string</span></span>|<span data-ttu-id="caea4-119">指定放在電子郵件地址**ReplyTo**標頭欄位的電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="caea4-119">Specifies the e-mail address placed on the **ReplyTo** header field of the e-mail message.</span></span>|  
|<span data-ttu-id="caea4-120">**[副本]**</span><span class="sxs-lookup"><span data-stu-id="caea4-120">**CC**</span></span>|<span data-ttu-id="caea4-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="caea4-121">xs:string</span></span>|<span data-ttu-id="caea4-122">指定的電子郵件地址或多個放**CC**標頭欄位的電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="caea4-122">Specifies the e-mail address or addresses placed on the **CC** header field of the e-mail message.</span></span>|  
|<span data-ttu-id="caea4-123">**日期**</span><span class="sxs-lookup"><span data-stu-id="caea4-123">**Date**</span></span>|<span data-ttu-id="caea4-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="caea4-124">xs:string</span></span>|<span data-ttu-id="caea4-125">指定的內容放在**日期**標頭欄位的電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="caea4-125">Specifies the content placed on the **Date** header field of the e-mail message.</span></span>|  
|<span data-ttu-id="caea4-126">**DispositionNotificationTo**</span><span class="sxs-lookup"><span data-stu-id="caea4-126">**DispositionNotificationTo**</span></span>|<span data-ttu-id="caea4-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="caea4-127">xs:string</span></span>|<span data-ttu-id="caea4-128">指定的內容放在**DispositionNotificationTo**標頭欄位的電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="caea4-128">Specifies the content placed on the **DispositionNotificationTo** header field of the e-mail message.</span></span>|  
|<span data-ttu-id="caea4-129">**標頭**</span><span class="sxs-lookup"><span data-stu-id="caea4-129">**Headers**</span></span>|<span data-ttu-id="caea4-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="caea4-130">xs:string</span></span>|<span data-ttu-id="caea4-131">指定電子郵件訊息所有標頭欄位的內容。</span><span class="sxs-lookup"><span data-stu-id="caea4-131">Specifies the content of all of the header fields of the e-mail message.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="caea4-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caea4-132">See Also</span></span>  
 [<span data-ttu-id="caea4-133">設定 POP3 配接器</span><span class="sxs-lookup"><span data-stu-id="caea4-133">Configuring the POP3 Adapter</span></span>](../core/configuring-the-pop3-adapter.md)