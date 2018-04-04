---
title: EDI 安全性的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d7f68bc-8460-4656-b9f2-955337458d78
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9517f6c5b1aeae06b5989eef12fe269f81a27c74
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="known-issues-with-edi-security"></a><span data-ttu-id="6b803-102">EDI 安全性的已知問題</span><span class="sxs-lookup"><span data-stu-id="6b803-102">Known Issues with EDI Security</span></span>
<span data-ttu-id="6b803-103">本主題描述的安全性的已知的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI 和 AS2 解決方案。</span><span class="sxs-lookup"><span data-stu-id="6b803-103">This topic describes known issues with the security of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2 solutions.</span></span>  
  
## <a name="biztalk-will-not-suspend-a-signed-message-from-a-party-for-which-no-certificate-is-set"></a><span data-ttu-id="6b803-104">BizTalk 不會擱置來自合作對象 (未設定任何憑證) 的已簽署訊息</span><span class="sxs-lookup"><span data-stu-id="6b803-104">BizTalk Will Not Suspend a Signed Message from a Party for which No Certificate is Set</span></span>  
 <span data-ttu-id="6b803-105">若您並未在合作對象設定簽章憑證 (位於合作對象之 [合作對象屬性] 頁面的 [憑證] 節點下)，但來自該合作對象的內送訊息已簽署，BizTalk Server 不會擱置該訊息，也不會根據不存在的憑證擲出例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6b803-105">If you do not set a signing certificate on a party (in the Certificate node of the party's Party Properties page), but an incoming message from that party is signed, BizTalk Server will not suspend the message and throw an exception based on the absence of the certificate.</span></span>  
  
 <span data-ttu-id="6b803-106">若您覆寫輸入訊息屬性 (位於 [做為 AS2 訊息傳送者的合作對象] 頁面上)，並清除 [訊息應該簽署] 屬性，則 BizTalk Server 會擱置已簽署的內送訊息。</span><span class="sxs-lookup"><span data-stu-id="6b803-106">If you override inbound message properties (on the Party as AS2 Message Sender page), and clear the "Message should be signed" property, BizTalk Server will suspend a signed incoming message.</span></span>  
  
## <a name="access-to-program-files-folder-can-be-limited-to-prevent-file-tampering"></a><span data-ttu-id="6b803-107">可限制程式檔案資料夾的存取，以防檔案遭竄改</span><span class="sxs-lookup"><span data-stu-id="6b803-107">Access to Program Files Folder Can Be Limited to Prevent File Tampering</span></span>  
 <span data-ttu-id="6b803-108">若含 BizTalk Server 可執行檔和 EDI 結構描述的 [程式檔案] 資料夾可供未經驗證的使用者使用，則這類使用者有可能修改那些檔案。</span><span class="sxs-lookup"><span data-stu-id="6b803-108">If the Program Files folder that contains BizTalk Server executables and EDI schemas is available to users who are not authenticated, those users can potentially modify those files.</span></span> <span data-ttu-id="6b803-109">為了防止此等威脅，您可以使用 [程式檔案] 資料夾的 [存取控制清單]\ (ACL)，限制只讓信任的使用者存取資料夾。</span><span class="sxs-lookup"><span data-stu-id="6b803-109">To protect against that threat, you can use Access Control Lists (ACLs) on the Program Files folder to limit access to trusted users.</span></span>  
  
## <a name="a-schema-with-a-long-field-can-be-susceptible-to-a-denial-of-service-attack"></a><span data-ttu-id="6b803-110">含長欄位的結構描述，可能容易遭拒絕服務攻擊</span><span class="sxs-lookup"><span data-stu-id="6b803-110">A Schema with a Long Field Can Be Susceptible to a Denial-of-Service Attack</span></span>  
 <span data-ttu-id="6b803-111">自訂結構描述如果欄位太長，可能容易遭拒絕服務攻擊利用。</span><span class="sxs-lookup"><span data-stu-id="6b803-111">A custom schema that has a field of very great length could potentially be exploited by a denial-of-service attack.</span></span> <span data-ttu-id="6b803-112">隨附的結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不需要大費周章，有的欄位，因此通常不會遭受此等攻擊。</span><span class="sxs-lookup"><span data-stu-id="6b803-112">Schemas that are shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] do not have fields with great lengths, and therefore are generally not susceptible to such an attack.</span></span>  
  
## <a name="message-processing-will-be-aborted-if-a-control-number-exceeds-its-maximum-length"></a><span data-ttu-id="6b803-113">若控制編號超過最大長度，訊息處理會中止</span><span class="sxs-lookup"><span data-stu-id="6b803-113">Message Processing Will Be Aborted If a Control Number Exceeds Its Maximum Length</span></span>  
 <span data-ttu-id="6b803-114">交換、群組或交易集之控制編號的最大長度都有限制。</span><span class="sxs-lookup"><span data-stu-id="6b803-114">An interchange, group, or transaction set control number has a limited maximum length.</span></span> <span data-ttu-id="6b803-115">若其中一個控制編號超過最大長度，則單一合作對象該編碼類型之所有訊息的處理都會中止。</span><span class="sxs-lookup"><span data-stu-id="6b803-115">If the length of one of these control numbers exceeds the maximum length, the processing of all messages of that encoding type for a single party will be aborted.</span></span> <span data-ttu-id="6b803-116">其他編碼類型 (例如 EDIFACT，而不是 X12) 的訊息不會受影響。</span><span class="sxs-lookup"><span data-stu-id="6b803-116">A message of another encoding type (EDIFACT instead of X12, for example) will not be affected.</span></span> <span data-ttu-id="6b803-117">這可能代表安全性弱點。</span><span class="sxs-lookup"><span data-stu-id="6b803-117">This could represent a security vulnerability.</span></span>  
  
 <span data-ttu-id="6b803-118">若序號的長度超過最大長度，則使用者必須重新設定受影響的合作對象之 EDI 屬性內的序號。</span><span class="sxs-lookup"><span data-stu-id="6b803-118">If the length of a sequence number exceeds the maximum length, the user has to reset the sequence number in the EDI Property for the party affected.</span></span> <span data-ttu-id="6b803-119">重新設定編號後，就可以再度處理該編碼類型的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="6b803-119">After the number has been reset, all messages of that encoding type can once again be processed.</span></span>  
  
 <span data-ttu-id="6b803-120">若是 X12 訊息，控制編號的最大長度為 9 個數字。</span><span class="sxs-lookup"><span data-stu-id="6b803-120">For X12 messages, the maximum length of a control number is nine digits.</span></span> <span data-ttu-id="6b803-121">若是 EDIFACT 訊息，控制編號的最大長度為三個欄位 14 個數字。</span><span class="sxs-lookup"><span data-stu-id="6b803-121">For EDIFACT message, the maximum length of a control number is 14 digits over three fields.</span></span>  
  
## <a name="using-the-edi-receive-pipeline-with-an-http-adapter-will-leave-the-connection-open-if-no-ack-is-sent"></a><span data-ttu-id="6b803-122">使用具 HTTP 配接器的 EDI 接收管線時，若沒有傳送任何通知，連線會維持開啟</span><span class="sxs-lookup"><span data-stu-id="6b803-122">Using the EDI Receive Pipeline with an HTTP Adapter Will Leave the Connection Open If No ACK Is Sent</span></span>  
 <span data-ttu-id="6b803-123">若您建立使用 EDIReceive 管線並具有 HTTP 傳輸類型的接收位置，可能會發生安全性問題。</span><span class="sxs-lookup"><span data-stu-id="6b803-123">A security issue could occur if you create a receive location that uses the EDIReceive pipeline and has a transport type of HTTP.</span></span> <span data-ttu-id="6b803-124">EDIReceive 管線不會產生 HTTP "200 OK" 通知。</span><span class="sxs-lookup"><span data-stu-id="6b803-124">The EdiReceive pipeline will not generate an HTTP "200 OK" acknowledgment.</span></span> <span data-ttu-id="6b803-125">若並未傳回 EDI 通知，則不會順利終止連線，而是會維持開啟。</span><span class="sxs-lookup"><span data-stu-id="6b803-125">If no EDI acknowledgment is returned, the connection will not be terminated gracefully, but will remain open.</span></span> <span data-ttu-id="6b803-126">如果超過逾時期間，則連線會逾時。</span><span class="sxs-lookup"><span data-stu-id="6b803-126">The connection will time out when the time-out period has expired.</span></span>  
  
 <span data-ttu-id="6b803-127">這個問題和 AS2EdiREceive 管線無關。</span><span class="sxs-lookup"><span data-stu-id="6b803-127">This is not an issue with the AS2EdiREceive pipeline.</span></span>  
  
## <a name="an-x12-encoded-message-is-suspended-if-port-based-authentication-is-enabled-and-biztalk-server-does-not-have-access-to-the-authorization-and-security-information"></a><span data-ttu-id="6b803-128">若以連接埠為基礎的驗證已啟用，且 BizTalk Server 無法存取授權和安全性資訊，X12 編碼訊息會遭擱置</span><span class="sxs-lookup"><span data-stu-id="6b803-128">An X12-Encoded Message Is Suspended If Port-Based Authentication Is Enabled and BizTalk Server Does Not Have Access to the Authorization and Security Information</span></span>  
 <span data-ttu-id="6b803-129">**徵狀**</span><span class="sxs-lookup"><span data-stu-id="6b803-129">**Symptom**</span></span>  
  
 <span data-ttu-id="6b803-130">已透過接收埠 (已啟用驗證) 接收訊息，卻無法判斷傳送訊息的合作對象時，BizTalk Server 會擱置該訊息。</span><span class="sxs-lookup"><span data-stu-id="6b803-130">When a message is received over a receive port for which authentication is enabled, and the party that sent the message cannot be determined, BizTalk Server will suspend the message.</span></span>  
  
 <span data-ttu-id="6b803-131">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="6b803-131">**Possible Cause**</span></span>  
  
 <span data-ttu-id="6b803-132">若接收埠已啟用驗證 (已清除接收埠的 [沒有驗證] 屬性)，則 BizTalk Server 需要 "ISA1-2" (授權辨識符號和資訊) 和 "ISA3-4" (安全性辨識符號和資訊) 屬性的設定，才能處理交換。</span><span class="sxs-lookup"><span data-stu-id="6b803-132">If authentication is enabled for a receive port (the "No Authentication" property for the receive port is cleared), BizTalk Server requires settings for the "ISA1-2 (Authorization qualifier and information)" and "ISA3-4 (Security qualifier and information)" properties in order to process the interchange.</span></span> <span data-ttu-id="6b803-133">合作對象的這些屬性，已經在 [合作對象做為交換傳送者] 的 [X12 交換處理屬性] 頁面中設定。</span><span class="sxs-lookup"><span data-stu-id="6b803-133">These properties are set for a party in the X12 Interchange Processing Properties page for the party as an interchange sender.</span></span> <span data-ttu-id="6b803-134">若 BizTalk Server 無法判斷這些屬性的值，就會擱置該訊息。</span><span class="sxs-lookup"><span data-stu-id="6b803-134">If BizTalk Server cannot determine the values of these properties, it will suspend the message.</span></span>  
  
 <span data-ttu-id="6b803-135">發生的情形有兩種。</span><span class="sxs-lookup"><span data-stu-id="6b803-135">This can occur in two ways.</span></span> <span data-ttu-id="6b803-136">其一，若 BizTalk Server 無法判斷傳送訊息的合作對象，就會使用 EDI 全域屬性，且無法存取授權和安全性設定，</span><span class="sxs-lookup"><span data-stu-id="6b803-136">In the first case, if BizTalk Server cannot determine the party that sent the message, it will use the EDI global properties and will not have access to the authorization and security settings.</span></span> <span data-ttu-id="6b803-137">因此就會擱置該訊息。</span><span class="sxs-lookup"><span data-stu-id="6b803-137">As a result, it will suspend the message.</span></span> <span data-ttu-id="6b803-138">其二，若 BizTalk Server 可判斷合作對象，但該合作對象的 ISA1-2 和 ISA3-4 屬性並未設定，BizTalk Server 便無法存取授權和安全性資訊，因此會擱置該訊息。</span><span class="sxs-lookup"><span data-stu-id="6b803-138">In the second case, if BizTalk Server determines the party, but the ISA1-2 and ISA3-4 properties for the party are not configured, BizTalk Server will again not have access to authorization and security information and will suspend the message.</span></span>  
  
 <span data-ttu-id="6b803-139">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="6b803-139">**Resolution**</span></span>  
  
 <span data-ttu-id="6b803-140">確保訊息的傳送合作對象一定要可辨識，且合作對象協議內務必定義 ISA1-2 和 ISA3-4 屬性。</span><span class="sxs-lookup"><span data-stu-id="6b803-140">Make sure that the sending party for the message can be identified and that the ISA1-2 and ISA3-4 properties are defined in the party agreement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b803-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b803-141">See Also</span></span>  
 [<span data-ttu-id="6b803-142">疑難排解 EDI 和 AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="6b803-142">Troubleshooting EDI and AS2 Solutions</span></span>](../core/troubleshooting-edi-and-as2-solutions.md)