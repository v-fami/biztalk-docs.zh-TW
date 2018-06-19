---
title: 減少阻絕服務攻擊 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IPSec, message protection
- messages, size
- security, configuring
- Authentication Required property
- security, Internet Information Services (IIS) Lockdown Tool
- security, Denial of Service attacks
- discretionary access control lists (DACLs)
- IPSec, data protection
- Internet Information Services (IIS) Lockdown Tool
- Denial of Service attacks
ms.assetid: f39c0d0a-b890-4c48-874d-5cafbc71473c
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a02e3eddcd43acf67e8e928e1a8f172c0019c616
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971740"
---
# <a name="mitigating-denial-of-service-attacks"></a><span data-ttu-id="b6e50-102">減少阻絕服務攻擊</span><span class="sxs-lookup"><span data-stu-id="b6e50-102">Mitigating Denial of Service Attacks</span></span>
<span data-ttu-id="b6e50-103">建議您使用下列防護技術，協助保護 BizTalk Server 與服務免於遭受拒絕服務的攻擊。</span><span class="sxs-lookup"><span data-stu-id="b6e50-103">It is recommended to use the following mitigation techniques to help protect your BizTalk servers and services against Denial of Service attacks.</span></span> <span data-ttu-id="b6e50-104">您必須決定其中哪些防護技術適用於您的環境。</span><span class="sxs-lookup"><span data-stu-id="b6e50-104">You must decide which of these mitigation techniques are appropriate for your environment.</span></span>  
  
-   <span data-ttu-id="b6e50-105">**接收埠中使用的所需的驗證屬性。**</span><span class="sxs-lookup"><span data-stu-id="b6e50-105">**Use the Authentication Required property in the receive port.**</span></span> <span data-ttu-id="b6e50-106">依照預設，BizTalk 會將它接收的所有訊息傳送到 MessageBox 資料庫，即使訊息是來自不明或無法解析的合作對象 (來賓使用者) 也一樣。若要減少潛在的攻擊者傳送大量訊息至 BizTalk Server，而灌爆 （塞滿） MessageBox 資料庫中，您可以使用**需要驗證**接收埠只接收中的屬性來自 BizTalk Server 知道的合作對象的訊息。</span><span class="sxs-lookup"><span data-stu-id="b6e50-106">By default, BizTalk sends all the messages it receives to the MessageBox database, even if they come from an unknown or unresolved party (Guest.) To mitigate the potential of an attacker sending a large number of messages to BizTalk Server and flooding (filling) the MessageBox database, you can use the **Authentication Required** property in the receive port to only receive messages that come from parties BizTalk Server knows.</span></span> <span data-ttu-id="b6e50-107">您可以選擇捨棄來自不明合作對象的訊息，或是擱置那些訊息。</span><span class="sxs-lookup"><span data-stu-id="b6e50-107">You can choose either to drop the messages coming from an unknown party or to suspend them.</span></span> <span data-ttu-id="b6e50-108">如需有關**需要驗證**屬性，請參閱[驗證訊息的傳送者](../core/authenticating-the-sender-of-a-message.md)。</span><span class="sxs-lookup"><span data-stu-id="b6e50-108">For more information about the **Authentication Required** property, see [Authenticating the Sender of a Message](../core/authenticating-the-sender-of-a-message.md).</span></span> <span data-ttu-id="b6e50-109">除了**需要驗證**屬性，您應該考慮使用外部機制，例如防火牆連接埠篩選或 IP 位址封鎖來防止阻絕服務攻擊。</span><span class="sxs-lookup"><span data-stu-id="b6e50-109">In addition to the **Authentication Required** property, you should consider the use of an external mechanism such as firewall port filtering or IP-address blocking to protect against Denial of Service attacks.</span></span>  
  
-   <span data-ttu-id="b6e50-110">**限制 BizTalk 可接收的訊息大小。**</span><span class="sxs-lookup"><span data-stu-id="b6e50-110">**Limit the size of the messages that BizTalk can receive.**</span></span> <span data-ttu-id="b6e50-111">例如，當您使用 SOAP 接收配接器，您可以避免接收非常大型的訊息大小的 maxRequestLength 屬性設定\<httpRuntime\>項目為可接受的大小。</span><span class="sxs-lookup"><span data-stu-id="b6e50-111">For example, when you use the SOAP receive adapter, you can avoid receiving very large messages size by setting the maxRequestLength attribute in the \<httpRuntime\> element to an acceptable size.</span></span> <span data-ttu-id="b6e50-112">\<HttpRuntime\>項目會定義在 Machine.config 檔案中，位於\<*磁碟機*\>:\\<*Windows目錄*\>\Microsoft.NET\Framework\vX.X.XXXXX\CONFIG 目錄。</span><span class="sxs-lookup"><span data-stu-id="b6e50-112">The \<httpRuntime\> element is defined in the Machine.config file, which is located in the \<*drive*\>:\\<*Windows directory*\>\Microsoft.NET\Framework\vX.X.XXXXX\CONFIG directory.</span></span> <span data-ttu-id="b6e50-113">如需有關\<httpRuntime\>項目，請參閱 Microsoft MSDN 網站，網址[http://go.microsoft.com/fwlink/?LinkId=60948](http://go.microsoft.com/fwlink/?LinkId=60948)。</span><span class="sxs-lookup"><span data-stu-id="b6e50-113">For more information about \<httpRuntime\> element, see the Microsoft MSDN Web site at [http://go.microsoft.com/fwlink/?LinkId=60948](http://go.microsoft.com/fwlink/?LinkId=60948).</span></span>  
  
-   <span data-ttu-id="b6e50-114">**使用強式 Dacl，為接收位置。**</span><span class="sxs-lookup"><span data-stu-id="b6e50-114">**Use strong DACLs for receive locations.**</span></span> <span data-ttu-id="b6e50-115">建議您在接收位置的放置位置使用強式判別存取控制清單 (DACL)。</span><span class="sxs-lookup"><span data-stu-id="b6e50-115">It is recommended that you use strong discretionary access control lists (DACLs) in the drop locations for the receive locations.</span></span> <span data-ttu-id="b6e50-116">例如，您必須在目錄中使用強式 DACL，檔案接收位置在此目錄拾取訊息，使得只有授權的使用者可以在此位置放置訊息。</span><span class="sxs-lookup"><span data-stu-id="b6e50-116">For example, you must use strong DACLs in the directory from which the file receive location picks up messages, so that only authorized users can drop messages in this location.</span></span>  
  
-   <span data-ttu-id="b6e50-117">**使用 IPSec。**</span><span class="sxs-lookup"><span data-stu-id="b6e50-117">**Use IPSec.**</span></span> <span data-ttu-id="b6e50-118">若您不使用硬體或軟體防火牆，請使用網際網路通訊協定安全性 (IPSec) 來協助保護 BizTalk 將訊息從伺服器傳送到另一個伺服器時訊息與資料的安全。</span><span class="sxs-lookup"><span data-stu-id="b6e50-118">If you do not use hardware or software firewalls, use Internet Protocol security (IPSec) to help protect the messages and data as BizTalk Server transfers it from one server to another.</span></span> <span data-ttu-id="b6e50-119">如需 IPSec 的詳細資訊，請參閱 Microsoft 下載中心[http://go.microsoft.com/fwlink/?LinkId=60949](http://go.microsoft.com/fwlink/?LinkId=60949)。</span><span class="sxs-lookup"><span data-stu-id="b6e50-119">For more information about IPSec, see the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkId=60949](http://go.microsoft.com/fwlink/?LinkId=60949).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e50-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="b6e50-120">See Also</span></span>  
 <span data-ttu-id="b6e50-121">[識別潛在威脅](../core/identifying-potential-threats.md) </span><span class="sxs-lookup"><span data-stu-id="b6e50-121">[Identifying Potential Threats](../core/identifying-potential-threats.md) </span></span>  
 [<span data-ttu-id="b6e50-122">安全性規劃</span><span class="sxs-lookup"><span data-stu-id="b6e50-122">Planning for Security</span></span>](../core/planning-for-security.md)