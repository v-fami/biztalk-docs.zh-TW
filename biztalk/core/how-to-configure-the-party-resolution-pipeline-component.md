---
title: 如何設定合作對象解析管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- authenticating, Partner Management
- Party Resolution [pipeline component], configuring
- Partner Management, authenticating
- pipeline components, Party Resolution
ms.assetid: 0ebd30f7-3a6b-4457-8e30-80bf81fbd28d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0c78792cd7c61ed1297954625fbd7da5aedfa04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248214"
---
# <a name="how-to-configure-the-party-resolution-pipeline-component"></a><span data-ttu-id="44efd-102">如何設定合作對象解析管線元件</span><span class="sxs-lookup"><span data-stu-id="44efd-102">How to Configure the Party Resolution Pipeline Component</span></span>
<span data-ttu-id="44efd-103">合作對象解析管線元件可用以將使用者安全性識別碼與用戶端的憑證主旨對應到 BizTalk Server 合作對象。</span><span class="sxs-lookup"><span data-stu-id="44efd-103">The Party Resolution pipeline component is used to map the user security ID and the certificate subject for the client to a BizTalk Server party.</span></span> <span data-ttu-id="44efd-104">對應可用以強制驗證傳送訊息至 BizTalk Server 的合作對象。</span><span class="sxs-lookup"><span data-stu-id="44efd-104">The mapping is used to enforce authentication of the parties who send messages to BizTalk Server.</span></span> <span data-ttu-id="44efd-105">如需有關夥伴管理的詳細資訊，請參閱[如何建立協議](http://msdn.microsoft.com/library/f8608cf7-8ac5-4f02-805e-5a0bdf19ca8c)。</span><span class="sxs-lookup"><span data-stu-id="44efd-105">For more information about partner management, see[How to Create an Agreement](http://msdn.microsoft.com/library/f8608cf7-8ac5-4f02-805e-5a0bdf19ca8c).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44efd-106">若要啟用合作對象解析管線元件以驗證 Windows 使用者，您必須將 WindowsUser 別名新增至合作對象。</span><span class="sxs-lookup"><span data-stu-id="44efd-106">To enable the Party Resolution pipeline component to validate a Windows user, you must add the WindowsUser alias to a party.</span></span> <span data-ttu-id="44efd-107">如需詳細資訊，請參閱[合作對象解析管線元件](../core/party-resolution-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="44efd-107">For more information, see [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md).</span></span>  
  
### <a name="to-configure-the-properties-for-the-party-resolution-pipeline-component"></a><span data-ttu-id="44efd-108">設定合作對象解析管線元件的屬性</span><span class="sxs-lookup"><span data-stu-id="44efd-108">To configure the properties for the Party Resolution pipeline component</span></span>  
  
1.  <span data-ttu-id="44efd-109">將合作對象解析管線元件拖曳至接收管線的解析合作對象階段。</span><span class="sxs-lookup"><span data-stu-id="44efd-109">Drag the Party Resolution pipeline component into the ResolveParty stage of a receive pipeline.</span></span>  
  
2.  <span data-ttu-id="44efd-110">在 [屬性] 視窗中**管線元件屬性**區段中，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="44efd-110">In the Properties window, in the **Pipeline Component Properties** section, do the following.</span></span>  
  
    |<span data-ttu-id="44efd-111">使用</span><span class="sxs-lookup"><span data-stu-id="44efd-111">Use this</span></span>|<span data-ttu-id="44efd-112">動作</span><span class="sxs-lookup"><span data-stu-id="44efd-112">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="44efd-113">**解析合作對象憑證**</span><span class="sxs-lookup"><span data-stu-id="44efd-113">**Resolve Party By Certificate**</span></span>|<span data-ttu-id="44efd-114">設定為**True**如果您想要啟用合作對象解析之合作對象接收訊息的簽章憑證的指紋為依據。</span><span class="sxs-lookup"><span data-stu-id="44efd-114">Set to **True** if you want to enable party resolution based on the thumbprint of the signature certificate from the party from where the messages are received.</span></span><br /><br /> <span data-ttu-id="44efd-115">預設值： **，則為 True**</span><span class="sxs-lookup"><span data-stu-id="44efd-115">Default value: **True**</span></span>|  
    |<span data-ttu-id="44efd-116">**解析合作對象的 SID**</span><span class="sxs-lookup"><span data-stu-id="44efd-116">**Resolve Party By SID**</span></span>|<span data-ttu-id="44efd-117">設定為**True**如果您想要讓合作對象解析以傳送者帳戶的安全性識別碼 (SID) 為基礎。</span><span class="sxs-lookup"><span data-stu-id="44efd-117">Set to **True** if you want to enable party resolution based on the security identifier (SID) of the sender account.</span></span><br /><br /> <span data-ttu-id="44efd-118">如果這兩個屬性會設為**True**、**依憑證解析合作對象**屬性會優先於**依 SID 解析合作對象**屬性，也就是說，如果這兩個憑證和 SID 都可用，會使用憑證主旨。</span><span class="sxs-lookup"><span data-stu-id="44efd-118">If both properties are set to **True**, the **Resolve Party By Certificate** property takes precedence over the **Resolve Party By SID** property, meaning that if both the certificate and the SID are available, the certificate subject is used.</span></span> <span data-ttu-id="44efd-119">如果無法使用憑證主旨解析合作對象，元件不會回到**依 SID 解析合作對象**屬性，而且預設值 (-1-5-7) 加上戳記的**BTS。SourcePartyID**。</span><span class="sxs-lookup"><span data-stu-id="44efd-119">If the party cannot be resolved by using the certificate subject, the component does not fall back to the **Resolve Party By SID** property, and the default value (s-1-5-7) is stamped for **BTS.SourcePartyID**.</span></span><br /><br /> <span data-ttu-id="44efd-120">預設值： **，則為 True**</span><span class="sxs-lookup"><span data-stu-id="44efd-120">Default value: **True**</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="44efd-121">如果您使用 BizTalk 訊息佇列配接器，若要解析合作對象為基礎的使用者名稱中設定**依憑證解析合作對象**至**False**和**依 SID 解析合作對象**至**True**。</span><span class="sxs-lookup"><span data-stu-id="44efd-121">If you use the BizTalk Message Queuing adapter and want to resolve the party based on user name, set **Resolve Party By Certificate** to **False** and **Resolve Party By SID** to **True**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44efd-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44efd-122">See Also</span></span>  
 <span data-ttu-id="44efd-123">[合作對象解析管線元件](../core/party-resolution-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="44efd-123">[Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md) </span></span>  
 <span data-ttu-id="44efd-124">[設定原生管線元件](../core/configuring-native-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="44efd-124">[Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md) </span></span>  
 [<span data-ttu-id="44efd-125">自訂合作對象解析 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="44efd-125">Custom Party Resolution (BizTalk Server Sample)</span></span>](../core/custom-party-resolution-biztalk-server-sample.md)