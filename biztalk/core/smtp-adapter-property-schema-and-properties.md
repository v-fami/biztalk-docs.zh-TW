---
title: SMTP 配接器屬性結構描述和屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UserName property, SMTP adapters
- EmailBodyTextCharset property [SMTP adapters]
- configuring [SMTP adapters], properties
- Subject property [SMTP adapters]
- EmailBodyFileCharset property [SMTP adapters]
- Attachments property [SMTP adapters]
- SMTP adapters, schemas
- EmailBodyText property [SMTP adapters]
- configuring [SMTP adapters], schemas
- CC property [SMTP adapters]
- ReadReceipt property [SMTP adapters]
- Password property [SMTP adapters]
- ReplyBy property [SMTP adapters]
- DeliveryReceipt property [SMTP adapters]
- SMTP adapters, properties
- SMTPAuthenticate property [SMTP adapters]
- EmailBodyFile property [SMTP adapters]
- schemas, SMTP adapters
- SMTPHost property [SMTP adapters]
- From property [SMTP adapters]
- MessagePartsAttachments property [SMTP adapters]
ms.assetid: 6d062fb6-d728-4525-8f0d-bd3f0f8ff7ca
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09f7dfa67bfad53e43a4a6678ff6ad67705e0e27
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278670"
---
# <a name="smtp-adapter-property-schema-and-properties"></a><span data-ttu-id="c739b-102">SMTP 配接器屬性結構描述和屬性</span><span class="sxs-lookup"><span data-stu-id="c739b-102">SMTP Adapter Property Schema and Properties</span></span>
<span data-ttu-id="c739b-103">下表列出 SMTP 配接器屬性結構描述中的屬性。</span><span class="sxs-lookup"><span data-stu-id="c739b-103">The following table lists the properties in the SMTP adapter property schema.</span></span>  
  
 <span data-ttu-id="c739b-104">**命名空間：** http://schemas.microsoft.com/BizTalk/2003/smtp-properties</span><span class="sxs-lookup"><span data-stu-id="c739b-104">**Namespace:** http://schemas.microsoft.com/BizTalk/2003/smtp-properties</span></span>  
  
|<span data-ttu-id="c739b-105">名稱</span><span class="sxs-lookup"><span data-stu-id="c739b-105">Name</span></span>|<span data-ttu-id="c739b-106">型別</span><span class="sxs-lookup"><span data-stu-id="c739b-106">Type</span></span>|<span data-ttu-id="c739b-107">Description</span><span class="sxs-lookup"><span data-stu-id="c739b-107">Description</span></span>|  
|----------|----------|-----------------|  
|<span data-ttu-id="c739b-108">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="c739b-108">**Username**</span></span>|<span data-ttu-id="c739b-109">xs:string</span><span class="sxs-lookup"><span data-stu-id="c739b-109">xs:string</span></span>|<span data-ttu-id="c739b-110">指定要用於 SMTP 伺服器驗證的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="c739b-110">Specify the user name to use for authentication with the SMTP server.</span></span>|  
|<span data-ttu-id="c739b-111">**密碼**</span><span class="sxs-lookup"><span data-stu-id="c739b-111">**Password**</span></span>|<span data-ttu-id="c739b-112">xs:string</span><span class="sxs-lookup"><span data-stu-id="c739b-112">xs:string</span></span>|<span data-ttu-id="c739b-113">指定要用於 SMTP 伺服器驗證的密碼。</span><span class="sxs-lookup"><span data-stu-id="c739b-113">Specify the password to use for authentication with the SMTP server.</span></span>|  
|<span data-ttu-id="c739b-114">**SMTPHost**</span><span class="sxs-lookup"><span data-stu-id="c739b-114">**SMTPHost**</span></span>|<span data-ttu-id="c739b-115">xs:string</span><span class="sxs-lookup"><span data-stu-id="c739b-115">xs:string</span></span>|<span data-ttu-id="c739b-116">指定傳送訊息時要使用的 SMTP 伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="c739b-116">Specify the name of the SMTP server to use when sending messages.</span></span>|  
|<span data-ttu-id="c739b-117">**來源**</span><span class="sxs-lookup"><span data-stu-id="c739b-117">**From**</span></span>|<span data-ttu-id="c739b-118">xs:string</span><span class="sxs-lookup"><span data-stu-id="c739b-118">xs:string</span></span>|<span data-ttu-id="c739b-119">指定要置於 SMTP 電子郵件地址**從**標頭。</span><span class="sxs-lookup"><span data-stu-id="c739b-119">Specify the e-mail address to place on the SMTP **From** header.</span></span>|  
|<span data-ttu-id="c739b-120">**[副本]**</span><span class="sxs-lookup"><span data-stu-id="c739b-120">**CC**</span></span>|<span data-ttu-id="c739b-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c739b-121">xs:string</span></span>|<span data-ttu-id="c739b-122">指定傳送訊息副本的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="c739b-122">Specify the e-mail address to send a copy of the message.</span></span>|  
|<span data-ttu-id="c739b-123">**主旨**</span><span class="sxs-lookup"><span data-stu-id="c739b-123">**Subject**</span></span>|<span data-ttu-id="c739b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c739b-124">xs:string</span></span>|<span data-ttu-id="c739b-125">指定訊息的主旨標題。</span><span class="sxs-lookup"><span data-stu-id="c739b-125">Specify the subject header for the message.</span></span>|  
|<span data-ttu-id="c739b-126">**SMTPAuthenticate**</span><span class="sxs-lookup"><span data-stu-id="c739b-126">**SMTPAuthenticate**</span></span>|<span data-ttu-id="c739b-127">xs:int</span><span class="sxs-lookup"><span data-stu-id="c739b-127">xs:int</span></span>|<span data-ttu-id="c739b-128">指定要用於 SMTP 伺服器的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="c739b-128">Specify the type of authentication to use with the SMTP server.</span></span>|  
|<span data-ttu-id="c739b-129">**ReadReceipt**</span><span class="sxs-lookup"><span data-stu-id="c739b-129">**ReadReceipt**</span></span>|<span data-ttu-id="c739b-130">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="c739b-130">xs:boolean</span></span>|<span data-ttu-id="c739b-131">指定是否在訊息被讀取時傳送確認電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="c739b-131">Specify whether to send a confirmation e-mail message when the message is read.</span></span>|  
|<span data-ttu-id="c739b-132">**DeliveryReceipt**</span><span class="sxs-lookup"><span data-stu-id="c739b-132">**DeliveryReceipt**</span></span>|<span data-ttu-id="c739b-133">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="c739b-133">xs:boolean</span></span>|<span data-ttu-id="c739b-134">指定傳遞訊息之後是否傳送確認電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="c739b-134">Specify whether to send a confirmation e-mail message after delivery of the message.</span></span>|  
|<span data-ttu-id="c739b-135">**EmailBodyText**</span><span class="sxs-lookup"><span data-stu-id="c739b-135">**EmailBodyText**</span></span>|<span data-ttu-id="c739b-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="c739b-136">xs:string</span></span>|<span data-ttu-id="c739b-137">指定傳送的電子郵件內文所使用的文字。</span><span class="sxs-lookup"><span data-stu-id="c739b-137">Specify text to be used for the body of the e-mail being sent.</span></span>|  
|<span data-ttu-id="c739b-138">**EmailBodyTextCharset**</span><span class="sxs-lookup"><span data-stu-id="c739b-138">**EmailBodyTextCharset**</span></span>|<span data-ttu-id="c739b-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="c739b-139">xs:string</span></span>|<span data-ttu-id="c739b-140">指定要用於編碼傳送之電子郵件內文的字元集**EmailBodyText**選項使用。</span><span class="sxs-lookup"><span data-stu-id="c739b-140">Specify the character set to use for encoding the body of the e-mail being sent when the **EmailBodyText** option is used.</span></span> <span data-ttu-id="c739b-141">SMTP 配接器會將轉換**EmailBodyText**設定所指定的字元**EmailBodyTextCharset**。</span><span class="sxs-lookup"><span data-stu-id="c739b-141">The SMTP adapter will convert the **EmailBodyText** to the character set specified by **EmailBodyTextCharset**.</span></span>|  
|<span data-ttu-id="c739b-142">**EmailBodyFile**</span><span class="sxs-lookup"><span data-stu-id="c739b-142">**EmailBodyFile**</span></span>|<span data-ttu-id="c739b-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="c739b-143">xs:string</span></span>|<span data-ttu-id="c739b-144">指定將用於傳送的電子郵件內文的檔案內容，以及檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="c739b-144">Specifies that the contents of a file will be used for the body of the e-mail being sent and the full path to the file.</span></span> <span data-ttu-id="c739b-145">在執行階段，SMTP 配接器的主控件必須可以存取此路徑。</span><span class="sxs-lookup"><span data-stu-id="c739b-145">This path must be accessible to the host for the SMTP adapter at run time.</span></span>|  
|<span data-ttu-id="c739b-146">**EmailBodyFileCharset**</span><span class="sxs-lookup"><span data-stu-id="c739b-146">**EmailBodyFileCharset**</span></span>|<span data-ttu-id="c739b-147">xs:string</span><span class="sxs-lookup"><span data-stu-id="c739b-147">xs:string</span></span>|<span data-ttu-id="c739b-148">指定要用於編碼傳送之電子郵件內文的字元集**EmailBodyFile**屬性設定。</span><span class="sxs-lookup"><span data-stu-id="c739b-148">Specify the character set to use for encoding the body of the e-mail being sent if the **EmailBodyFile** property is set.</span></span> <span data-ttu-id="c739b-149">SMTP 配接器不會在檔案執行任何轉換；檔案必須已經使用此字元集編碼。</span><span class="sxs-lookup"><span data-stu-id="c739b-149">The SMTP adapter will not perform any conversion on the file; the file must already be encoded in this character set.</span></span> <span data-ttu-id="c739b-150">若檔案有一個「位元順序標記」(Byte-Order-Mark，BOM)，SMTP 配接器會移除它。</span><span class="sxs-lookup"><span data-stu-id="c739b-150">If the file has a Byte-Order-Mark (BOM), the SMTP adapter will remove it.</span></span>|  
|<span data-ttu-id="c739b-151">**附加檔案**</span><span class="sxs-lookup"><span data-stu-id="c739b-151">**Attachments**</span></span>|<span data-ttu-id="c739b-152">xs:string</span><span class="sxs-lookup"><span data-stu-id="c739b-152">xs:string</span></span>|<span data-ttu-id="c739b-153">指定要附加一或多個檔案至電子郵件訊息，以及檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="c739b-153">Specifies that a file or files will be attached to the e-mail message and the full path to the file or files.</span></span> <span data-ttu-id="c739b-154">在執行階段，SMTP 配接器的主控件必須可以存取指定的一或多個路徑。</span><span class="sxs-lookup"><span data-stu-id="c739b-154">The specified path or paths must be accessible to the host for the SMTP adapter at run time.</span></span>|  
|<span data-ttu-id="c739b-155">**MessagePartsAttachments**</span><span class="sxs-lookup"><span data-stu-id="c739b-155">**MessagePartsAttachments**</span></span>|<span data-ttu-id="c739b-156">xs:unsignedInt</span><span class="sxs-lookup"><span data-stu-id="c739b-156">xs:unsignedInt</span></span>|<span data-ttu-id="c739b-157">指定如何將 BizTalk 訊息部分附加到電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="c739b-157">Specify how BizTalk message parts are attached to the e-mail message.</span></span>|  
|<span data-ttu-id="c739b-158">**ReplyBy**</span><span class="sxs-lookup"><span data-stu-id="c739b-158">**ReplyBy**</span></span>|<span data-ttu-id="c739b-159">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="c739b-159">xs:dateTime</span></span>|<span data-ttu-id="c739b-160">指定的 dateTime 值**回覆給**外寄電子郵件訊息中的標頭。</span><span class="sxs-lookup"><span data-stu-id="c739b-160">Specify a dateTime value for the **Reply-To** header in the outgoing e-mail message.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c739b-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c739b-161">See Also</span></span>  
 [<span data-ttu-id="c739b-162">設定 SMTP 配接器</span><span class="sxs-lookup"><span data-stu-id="c739b-162">Configuring the SMTP Adapter</span></span>](../core/configuring-the-smtp-adapter.md)