---
title: SMTP 配接器安全性建議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [SMTP adapters], security
- SMTP adapters, security
- security, SMTP adapters
ms.assetid: 45f13744-a0eb-4b4e-85cd-6b862b384ad5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca1aeed0ad8c80cc32d333aeef37d1da6feabfc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276494"
---
# <a name="smtp-adapter-security-recommendations"></a><span data-ttu-id="2051e-102">SMTP 配接器安全性建議</span><span class="sxs-lookup"><span data-stu-id="2051e-102">SMTP Adapter Security Recommendations</span></span>
<span data-ttu-id="2051e-103">您使用 SMTP 配接器透過 Simple Mail Transfer Protocol (SMTP) 通訊協定，交換執行 BizTalk Server 的伺服器與其他應用程式之間的資訊。</span><span class="sxs-lookup"><span data-stu-id="2051e-103">You use the SMTP adapter to exchange information between a server running BizTalk Server and other applications by means of the Simple Mail Transfer Protocol (SMTP) protocol.</span></span> <span data-ttu-id="2051e-104">BizTalk Server 可建立電子郵件訊息並將它傳送到指定的電子郵件地址，將訊息傳送到其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="2051e-104">BizTalk Server can send messages to other applications by creating an e-mail message and delivering it to a specified e-mail address.</span></span> <span data-ttu-id="2051e-105">您只可將 SMTP 配接器用於傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="2051e-105">You can use the SMTP adapter only for sending messages.</span></span> <span data-ttu-id="2051e-106">如需有關 SMTP 配接器的詳細資訊，請參閱[SMTP 配接器](../core/smtp-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="2051e-106">For more information about the SMTP adapter, see [SMTP Adapter](../core/smtp-adapter.md).</span></span>  
  
 <span data-ttu-id="2051e-107">為執行 SMTP 配接器的主控件執行個體設定服務帳戶時，必須指定對遠端 SMTP 伺服器使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="2051e-107">When you configure the service account for the host instance running the SMTP adapter, you need to specify the type of authentication you want to use with the remote SMTP server.</span></span> <span data-ttu-id="2051e-108">驗證選項有基本驗證 (純文字)、NTLM (使用目前認證) 或無 (若 SMTP 伺服器不需要驗證)。</span><span class="sxs-lookup"><span data-stu-id="2051e-108">The authentication options are basic authentication (clear text), NTLM (by using current credentials), or none if authentication is not required by the SMTP server.</span></span>  
  
 <span data-ttu-id="2051e-109">使用 SMTP 配接器傳送訊息時，BizTalk Server 預設會以純文字傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="2051e-109">When you send a message by using the SMTP adapter, BizTalk Server sends the message in clear text by default.</span></span> <span data-ttu-id="2051e-110">若使用具有 S/MIME 編碼器元件的管線，在您將訊息傳送到 SMTP 伺服器之前可以先加密。</span><span class="sxs-lookup"><span data-stu-id="2051e-110">If you use a pipeline that has an S/MIME encoder component, you can encrypt the message before you send it to the SMTP server.</span></span> <span data-ttu-id="2051e-111">不過，SMTP 標頭仍會是純文字。</span><span class="sxs-lookup"><span data-stu-id="2051e-111">However, the SMTP header is still in clear text.</span></span>  
  
 <span data-ttu-id="2051e-112">若要稽核 BizTalk Server 傳送的電子郵件訊息，應使用 SMTP 配接器連接到自己的 SMTP 伺服器，即可在此伺服器內稽核訊息。</span><span class="sxs-lookup"><span data-stu-id="2051e-112">If you want to audit the e-mail messages that BizTalk Server sends, you should use the SMTP adapter to connect to your own SMTP server, where you can then audit the messages.</span></span>  
  
 <span data-ttu-id="2051e-113">SMTP 配接器不支援安全通訊端層 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="2051e-113">The SMTP adapter does not support Secure Sockets Layer (SSL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2051e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2051e-114">See Also</span></span>  
 <span data-ttu-id="2051e-115">[接收和傳送伺服器的連接埠](../core/ports-for-the-receive-and-send-servers.md) </span><span class="sxs-lookup"><span data-stu-id="2051e-115">[Ports for the Receive and Send Servers](../core/ports-for-the-receive-and-send-servers.md) </span></span>  
 [<span data-ttu-id="2051e-116">最小安全性使用者權限</span><span class="sxs-lookup"><span data-stu-id="2051e-116">Minimum Security User Rights</span></span>](../core/minimum-security-user-rights.md)