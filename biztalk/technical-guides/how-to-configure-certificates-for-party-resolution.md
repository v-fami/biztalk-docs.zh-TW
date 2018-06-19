---
title: 如何設定合作對象解析的憑證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 060101c1-14f3-4600-a18e-48a160d59bca
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 153c8ccce1fafbe32c51b1c048fad4081f5b0b0b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297718"
---
# <a name="how-to-configure-certificates-for-party-resolution"></a><span data-ttu-id="f7e1a-102">如何設定合作對象解析的憑證</span><span class="sxs-lookup"><span data-stu-id="f7e1a-102">How to Configure Certificates for Party Resolution</span></span>
<span data-ttu-id="f7e1a-103">當您使用 BizTalk 總管 中建立合作對象時，您可以設定合作對象，以便使用數位簽章來解析合作對象。</span><span class="sxs-lookup"><span data-stu-id="f7e1a-103">When you use BizTalk Explorer to configure a party, you can configure the party so that the party is resolved by using its digital signature.</span></span> <span data-ttu-id="f7e1a-104">如果您設定合作對象如此一來，當[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]收到訊息時，它會使用公開金鑰憑證，來決定是誰傳送訊息，並在已知的合作對象解析寄件者[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="f7e1a-104">If you configure the party this way, when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives a message, it will use the public key certificate to determine who sent the message, and to resolve the sender to a known party in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f7e1a-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="f7e1a-105">Prerequisites</span></span>  
 <span data-ttu-id="f7e1a-106">若要執行本主題中的程序，您必須登入的成員身分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="f7e1a-106">To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-party-resolution-to-use-a-certificate"></a><span data-ttu-id="f7e1a-107">若要設定合作對象解析，以使用憑證</span><span class="sxs-lookup"><span data-stu-id="f7e1a-107">To configure party resolution to use a certificate</span></span>  
  
1.  <span data-ttu-id="f7e1a-108">開啟**合作對象屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f7e1a-108">Open the **Party Properties** dialog box.</span></span>  
  
2.  <span data-ttu-id="f7e1a-109">按一下**憑證**索引標籤，然後再按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="f7e1a-109">Click the **Certificate** tab, and then click **Browse**.</span></span>  
  
3.  <span data-ttu-id="f7e1a-110">選取的憑證。</span><span class="sxs-lookup"><span data-stu-id="f7e1a-110">Select a certificate.</span></span>  
  
4.  <span data-ttu-id="f7e1a-111">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f7e1a-111">Click **OK**.</span></span>