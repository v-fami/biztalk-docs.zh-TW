---
title: "SMTP 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SMTP adapters, about SMTP adapters
- SMTP adapters, authenticating
- send adapters, SMTP adapters
- authenticating, SMTP adapters
- SMTP adapters
- SMTP adapters, send adapters
ms.assetid: b712f76d-3ce4-4780-9627-951e5951bd8a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0d0d16bf266d0b636aa9955b5c25b37d9ab54d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="smtp-adapter"></a><span data-ttu-id="14b67-102">SMTP 配接器</span><span class="sxs-lookup"><span data-stu-id="14b67-102">SMTP Adapter</span></span>
<span data-ttu-id="14b67-103">您可以使用「簡易郵件傳送通訊協定」(SMTP) 配接器在執行 Microsoft BizTalk Server 的伺服器和其他應用程式之間，利用 SMTP 通訊協定的方式來交換資訊。</span><span class="sxs-lookup"><span data-stu-id="14b67-103">You use the Simple Mail Transfer Protocol (SMTP) adapter to exchange information between a server running Microsoft BizTalk Server and other applications by means of the SMTP protocol.</span></span> <span data-ttu-id="14b67-104">BizTalk Server 可建立電子郵件訊息並將它傳送到指定的電子郵件地址，將訊息傳送到其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="14b67-104">BizTalk Server can send messages to other applications by creating an e-mail message and delivering it to a specified e-mail address.</span></span> <span data-ttu-id="14b67-105">SMTP 傳送配接器會在內部建立一個以 SMTP 為基礎的電子郵件訊息，並將訊息傳送到目標電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="14b67-105">Internally, the SMTP send adapter creates an SMTP-based e-mail message and sends it to a target e-mail address.</span></span> <span data-ttu-id="14b67-106">目標電子郵件地址是 SMTP 配接器的一個屬性。</span><span class="sxs-lookup"><span data-stu-id="14b67-106">The target e-mail address is a property of the SMTP adapter.</span></span> <span data-ttu-id="14b67-107">當您設定 SMTP 傳送埠時，「BizTalk 總管」會公開這個屬性。</span><span class="sxs-lookup"><span data-stu-id="14b67-107">BizTalk Explorer exposes this property when you configure the SMTP send port.</span></span>  
  
 <span data-ttu-id="14b67-108">SMTP 配接器支援在中的使用萬用字元**TO**， **FROM**， **CC**和**主旨**屬性，並將它們解析為其實際值。</span><span class="sxs-lookup"><span data-stu-id="14b67-108">The SMTP adapter supports wildcard characters in the **TO**, **FROM**, **CC** and **SUBJECT** properties, and resolves them to their actual values.</span></span> <span data-ttu-id="14b67-109">中的萬用字元**TO**， **FROM**，和**CC**屬性無法解決，SMTP 傳輸會記錄錯誤，並將訊息放入擱置的佇列或將訊息重新導向至備份傳輸。</span><span class="sxs-lookup"><span data-stu-id="14b67-109">If wildcard characters in the **TO**, **FROM**, and **CC** properties cannot be resolved, the SMTP transport logs an error and puts the message into the suspended queue or redirects the message to the backup transport.</span></span> <span data-ttu-id="14b67-110">如果無法解析萬用字元**主旨**屬性，將訊息傳送與**主旨**屬性所指定完全相同的屬性 （例如，"訊息 %messageid%")。</span><span class="sxs-lookup"><span data-stu-id="14b67-110">If the wildcard characters cannot be resolved in the **SUBJECT** property, the message is sent with the **SUBJECT** property specified exactly as in the property (for example, "Message %MessageID%").</span></span>  
  
 <span data-ttu-id="14b67-111">依照預設，SMTP 訊息的訊息文字是純文字。</span><span class="sxs-lookup"><span data-stu-id="14b67-111">By default, the message text of SMTP messages is plain text.</span></span> <span data-ttu-id="14b67-112">若要在訊息內文中使用 HTML，您可以設定配接器在訊息文字使用 HTML 檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="14b67-112">To use HTML in message bodies, you can configure the adapter to use the contents of an HTML file for the message text.</span></span>  
  
 <span data-ttu-id="14b67-113">如需有關 SMTP 安全性問題的詳細資訊，請參閱[SMTP 配接器安全性建議](../core/smtp-adapter-security-recommendations.md)。</span><span class="sxs-lookup"><span data-stu-id="14b67-113">For more information about SMTP security issues, see [SMTP Adapter Security Recommendations](../core/smtp-adapter-security-recommendations.md).</span></span>  
  
 <span data-ttu-id="14b67-114">SMTP 配接器僅由一個配接器和一個傳送配接器組成。</span><span class="sxs-lookup"><span data-stu-id="14b67-114">The SMTP adapter consists of only one adapter, a send adapter.</span></span> <span data-ttu-id="14b67-115">傳送配接器控制使用 SMTP 配接器的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="14b67-115">The send adapter controls the send ports that use the SMTP adapter.</span></span>  
  
 <span data-ttu-id="14b67-116">本主題討論通過 SMTP 傳送埠配接器的訊息流程。</span><span class="sxs-lookup"><span data-stu-id="14b67-116">This topic discusses the flow of a message through the SMTP send adapter.</span></span>  
  
 <span data-ttu-id="14b67-117">**SMTP 傳送配接器**</span><span class="sxs-lookup"><span data-stu-id="14b67-117">**SMTP Send Adapter**</span></span>  
  
 <span data-ttu-id="14b67-118">SMTP 傳送配接器從伺服器取得訊息，然後將它們公佈到 SMTP 伺服器，該伺服器會將訊息傳送給電子郵件收件者。</span><span class="sxs-lookup"><span data-stu-id="14b67-118">The SMTP send adapter gets messages from the server and posts them to an SMTP server that sends them to e-mail recipients.</span></span> <span data-ttu-id="14b67-119">SMTP 傳送配接器從 BizTalk 訊息物件的內文部分、從指定的檔案，或從設定配接器時可用的對話方塊中所輸入的文字，取得訊息內容。</span><span class="sxs-lookup"><span data-stu-id="14b67-119">The SMTP send adapter gets the message content from the body part of the BizTalk Message object, from a specified file, or from a text entered into a dialog box that is available when configuring the adapter.</span></span>  
  
 <span data-ttu-id="14b67-120">在 SMTP 傳送配接器成功將訊息公佈到 SMTP 伺服器之後，SMTP 傳送配接器會從 MessageBox 資料庫刪除訊息。</span><span class="sxs-lookup"><span data-stu-id="14b67-120">After the SMTP send adapter successfully posts a message onto the SMTP server, the SMTP send adapter deletes the message from the MessageBox database.</span></span>  
  
 <span data-ttu-id="14b67-121">SMTP 傳送配接器可以要求傳遞通知，並讀取透過 SMTP 傳送配接器傳送的訊息回條。</span><span class="sxs-lookup"><span data-stu-id="14b67-121">The SMTP send adapter can request delivery notification and read receipts for messages sent over the SMTP send adapter.</span></span> <span data-ttu-id="14b67-122">SMTP 配接器會將通知與讀取回條傳遞至 SMTP 上指定的位址**從**標頭。</span><span class="sxs-lookup"><span data-stu-id="14b67-122">The SMTP adapter delivers the notification and read receipt to the address specified on the SMTP **From** header.</span></span>  
  
 <span data-ttu-id="14b67-123">**SMTP 伺服器驗證**</span><span class="sxs-lookup"><span data-stu-id="14b67-123">**Authentication with SMTP Server**</span></span>  
  
 <span data-ttu-id="14b67-124">若您需要 SMTP 伺服器驗證，SMTP 傳送配接器會使用下列其中一個驗證類型：</span><span class="sxs-lookup"><span data-stu-id="14b67-124">If you require SMTP server authentication, the SMTP send adapter uses one of the following authentication types:</span></span>  
  
-   <span data-ttu-id="14b67-125">**基本。**</span><span class="sxs-lookup"><span data-stu-id="14b67-125">**Basic.**</span></span> <span data-ttu-id="14b67-126">SMTP 伺服器利用使用者提供的認證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="14b67-126">The SMTP server uses user-provided credentials for authentication.</span></span>  
  
-   <span data-ttu-id="14b67-127">**處理序帳戶 (NTLM)。**</span><span class="sxs-lookup"><span data-stu-id="14b67-127">**Process account (NTLM).**</span></span> <span data-ttu-id="14b67-128">SMTP 伺服器利用目前的程序認證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="14b67-128">The SMTP server uses current process credentials for authentication.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14b67-129">本節內容</span><span class="sxs-lookup"><span data-stu-id="14b67-129">In This Section</span></span>  
  
-   [<span data-ttu-id="14b67-130">設定 SMTP 配接器</span><span class="sxs-lookup"><span data-stu-id="14b67-130">Configuring the SMTP Adapter</span></span>](../core/configuring-the-smtp-adapter.md)  
  
-   [<span data-ttu-id="14b67-131">設定 SMTP 配接器時的限制</span><span class="sxs-lookup"><span data-stu-id="14b67-131">Restrictions When Configuring the SMTP Adapter</span></span>](../core/restrictions-when-configuring-the-smtp-adapter.md)  
  
-   [<span data-ttu-id="14b67-132">SMTP 配接器安全性建議</span><span class="sxs-lookup"><span data-stu-id="14b67-132">SMTP Adapter Security Recommendations</span></span>](../core/smtp-adapter-security-recommendations.md)