---
title: 在 BizTalk Server 中的安全性功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Server, security
- Master Secret server, security
- security, Master Secret server
- security, runtime
- security, data
- deploying, security
- security, configuring
- runtime, security
- security, security features
- security, messages
- security, access control
- security, about security
- access control
- security, deploying
- data, security
- messages, security
ms.assetid: 5ab15023-fa71-439e-b3aa-420fe28806fa
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d904bc842cb04bdf9c1457440c838c8a78e5c8f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992615"
---
# <a name="security-features-in-biztalk-server"></a><span data-ttu-id="0301b-102">BizTalk Server 中的安全性功能</span><span class="sxs-lookup"><span data-stu-id="0301b-102">Security Features in BizTalk Server</span></span>
<span data-ttu-id="0301b-103">Microsoft® BizTalk® Server 提供標準閘道，可以同時在內部網路中以及透過網際網路來傳送和接收文件。</span><span class="sxs-lookup"><span data-stu-id="0301b-103">Microsoft® BizTalk® Server provides a standard gateway for sending and receiving documents both within an intranet and through the Internet.</span></span> <span data-ttu-id="0301b-104">由於往返 BizTalk Server 所傳送的訊息可能在商務上具有重大性質，請務必考量因應措施，在這些訊息的傳輸過程中，以及在 BizTalk Server 加以處理和儲存時，協助保護訊息及其所含資訊的安全性。</span><span class="sxs-lookup"><span data-stu-id="0301b-104">Due to the possible business-critical nature of the messages sent to and from BizTalk Server, it is important to consider measures to help secure these messages and the information they contain both as they are in transit and while BizTalk Server processes and stores them.</span></span> <span data-ttu-id="0301b-105">本節將提供有關 BizTalk Server 安全性功能的詳細資訊，以及如何使用這些功能協助保護資料和環境的安全。</span><span class="sxs-lookup"><span data-stu-id="0301b-105">This section provides information about the BizTalk Server security features, and how you can use them to help secure your data and environment.</span></span>  
  
 <span data-ttu-id="0301b-106">BizTalk Server 使用下列措施協助您保護輸入和輸出訊息的安全、保護執行階段和組態資訊的安全，以及與其他應用程式和系統安全地整合在一起：</span><span class="sxs-lookup"><span data-stu-id="0301b-106">BizTalk Server uses the following measures to help secure inbound and outbound messages, to help secure the runtime and configuration information, and to help integrate securely with other applications and systems:</span></span>  
  
 <span data-ttu-id="0301b-107">**訊息安全性**</span><span class="sxs-lookup"><span data-stu-id="0301b-107">**Message security**</span></span>  
  
- <span data-ttu-id="0301b-108">驗證訊息傳送者。</span><span class="sxs-lookup"><span data-stu-id="0301b-108">Authenticating the sender of a message.</span></span> <span data-ttu-id="0301b-109">BizTalk Server 可以驗證訊息的傳送者 (使用憑證資訊或 Windows 整合安全性)，以驗證訊息傳送者的識別。</span><span class="sxs-lookup"><span data-stu-id="0301b-109">BizTalk Server can authenticate the sender of a message (either by using the certificate information or Windows integrated Security) in order to validate the identity of the sender of the message.</span></span> <span data-ttu-id="0301b-110">如需詳細資訊，請參閱 <<c0> [ 輸入訊息驗證](../core/inbound-message-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="0301b-110">For more information, see [Inbound Message Authentication](../core/inbound-message-authentication.md).</span></span>  
  
- <span data-ttu-id="0301b-111">訊息接收器的授權。</span><span class="sxs-lookup"><span data-stu-id="0301b-111">Authorizing of the receiver of a message.</span></span> <span data-ttu-id="0301b-112">在 BizTalk Server 收到訊息之後，BizTalk Server 就可以判斷哪些程序和使用者具有接收訊息的權限。</span><span class="sxs-lookup"><span data-stu-id="0301b-112">After BizTalk Server receives the message, BizTalk Server can determine what processes and users have permissions to receive the message.</span></span> <span data-ttu-id="0301b-113">如需詳細資訊，請參閱 <<c0> [ 授權訊息接收器](../core/authorizing-the-receiver-of-a-message.md)。</span><span class="sxs-lookup"><span data-stu-id="0301b-113">For more information, see [Authorizing the Receiver of a Message](../core/authorizing-the-receiver-of-a-message.md).</span></span>  
  
  <span data-ttu-id="0301b-114">**執行階段和組態安全性**</span><span class="sxs-lookup"><span data-stu-id="0301b-114">**Runtime and configuration security**</span></span>  
  
- <span data-ttu-id="0301b-115">**存取控制和保護資料安全。**</span><span class="sxs-lookup"><span data-stu-id="0301b-115">**Access control and securing data.**</span></span> <span data-ttu-id="0301b-116">BizTalk Server 使用存取控制來確保 BizTalk Server 程序有其適當限制，以及管控重大商務資訊的存取活動。</span><span class="sxs-lookup"><span data-stu-id="0301b-116">BizTalk Server uses access control to ensure that BizTalk Server processes have appropriate limits and that access to business critical information is controlled.</span></span> <span data-ttu-id="0301b-117">也就是說，BizTalk Server 可以確保使用者和帳戶僅具有足以執行其工作的最低使用者權限。</span><span class="sxs-lookup"><span data-stu-id="0301b-117">In other words, BizTalk Server ensures that users and accounts have the least user rights possible to enable them to do their tasks.</span></span> <span data-ttu-id="0301b-118">如需詳細資訊，請參閱 <<c0> [ 存取控制和資料安全性](../core/access-control-and-data-security.md)。</span><span class="sxs-lookup"><span data-stu-id="0301b-118">For more information, see [Access Control and Data Security](../core/access-control-and-data-security.md).</span></span>  
  
  <span data-ttu-id="0301b-119">**整合式的安全性**</span><span class="sxs-lookup"><span data-stu-id="0301b-119">**Integrated security**</span></span>  
  
- <span data-ttu-id="0301b-120">企業單一登入。</span><span class="sxs-lookup"><span data-stu-id="0301b-120">Enterprise Single Sign-On.</span></span> <span data-ttu-id="0301b-121">BizTalk Server 使用「企業單一登入」(SSO) 來確保完善加密配接器、傳送位置和接收位置所需的機密組態資訊，從而協助確保 BizTalk Server 能夠以安全的方式來儲存及傳輸這些資訊。</span><span class="sxs-lookup"><span data-stu-id="0301b-121">BizTalk Server uses Enterprise Single Sign-On (SSO) to ensure that it encrypts the sensitive configuration information that the adapters, send, and receive locations require, thus helping to ensure that BizTalk Server stores and transmit this information in a secure manner.</span></span> <span data-ttu-id="0301b-122">如需詳細資訊，請參閱 <<c0> [ 使用 SSO](../core/using-sso.md)。</span><span class="sxs-lookup"><span data-stu-id="0301b-122">For more information, see [Using SSO](../core/using-sso.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0301b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0301b-123">See Also</span></span>  
 <span data-ttu-id="0301b-124">[設計 BizTalk Server 的系統架構](../core/designing-the-system-architectures-for-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="0301b-124">[Designing the System Architectures for BizTalk Server](../core/designing-the-system-architectures-for-biztalk-server.md) </span></span>  
 <span data-ttu-id="0301b-125">[實作企業單一登入](../core/implementing-enterprise-single-sign-on.md) </span><span class="sxs-lookup"><span data-stu-id="0301b-125">[Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md) </span></span>  
 <span data-ttu-id="0301b-126">[規劃訊息安全性](../core/planning-message-security.md) </span><span class="sxs-lookup"><span data-stu-id="0301b-126">[Planning Message Security](../core/planning-message-security.md) </span></span>  
 [<span data-ttu-id="0301b-127">存取控制和資料安全性</span><span class="sxs-lookup"><span data-stu-id="0301b-127">Access Control and Data Security</span></span>](../core/access-control-and-data-security.md)   
