---
title: 設定 AS2 協議屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.admin.as2agreement.properties
ms.assetid: a62d8d2a-0b8d-4179-a48f-92f135b5787d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 960397bdce5090f57b9f2fe6882a27d313631df6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000831"
---
# <a name="configuring-as2-agreement-properties"></a><span data-ttu-id="894a6-102">設定 AS2 協議屬性</span><span class="sxs-lookup"><span data-stu-id="894a6-102">Configuring AS2 Agreement Properties</span></span>
<span data-ttu-id="894a6-103">本 節將說明 AS2 傳輸協議屬性 。</span><span class="sxs-lookup"><span data-stu-id="894a6-103">This section describes AS2 transport agreement properties.</span></span> <span data-ttu-id="894a6-104">在傳輸通訊協定設定當中，您還可以定義訊息是否應該經過簽章、加密等等。</span><span class="sxs-lookup"><span data-stu-id="894a6-104">As part of the transport protocol settings, you can also define whether the message should be signed, whether the message should be encrypted, etc.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="894a6-105">設定 AS2 協議是選擇性的動作。</span><span class="sxs-lookup"><span data-stu-id="894a6-105">Configuring an AS2 agreement is optional.</span></span> <span data-ttu-id="894a6-106">AS2 協議中會定義使用 AS2 通訊協定傳輸訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="894a6-106">An AS2 agreement defines how the messages are transferred using the AS2 protocol.</span></span> <span data-ttu-id="894a6-107">如果交易夥伴決定使用其他傳輸通訊協定來傳輸訊息，可以選擇不要定義 AS2 協議。</span><span class="sxs-lookup"><span data-stu-id="894a6-107">If the trading partners decide to use any other transport protocol to transfer messages, they can choose not to define an AS2 agreement.</span></span> <span data-ttu-id="894a6-108">不過，交易夥伴必須定義編碼協議，以控制訊息的構成與編碼方式。</span><span class="sxs-lookup"><span data-stu-id="894a6-108">However, the trading partners must define an encoding agreement that governs how the messages are formed and encoded.</span></span> <span data-ttu-id="894a6-109">如需編碼協議的詳細資訊，請參閱[設定編碼協議屬性](../core/configuring-encoding-agreement-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="894a6-109">For more information about encoding agreements, see [Configuring Encoding Agreement Properties](../core/configuring-encoding-agreement-properties.md).</span></span>  
> 
> [!IMPORTANT]
>  <span data-ttu-id="894a6-110">每次在協議中變更 AS2 設定時，您需要重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件執行個體，以便讓變更生效。</span><span class="sxs-lookup"><span data-stu-id="894a6-110">Every time you change an AS2 setting in an agreement, you must restart the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Host Instance for the changes to take effect.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="894a6-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="894a6-111">In This Section</span></span>  
  
-   [<span data-ttu-id="894a6-112">設定一般設定 (AS2)</span><span class="sxs-lookup"><span data-stu-id="894a6-112">Configuring General Settings (AS2)</span></span>](../core/configuring-general-settings-as2.md)  
  
-   [<span data-ttu-id="894a6-113">設定識別碼 (AS2)</span><span class="sxs-lookup"><span data-stu-id="894a6-113">Configuring Identifiers (AS2)</span></span>](../core/configuring-identifiers-as2.md)  
  
-   [<span data-ttu-id="894a6-114">設定驗證 (AS2)</span><span class="sxs-lookup"><span data-stu-id="894a6-114">Configuring Validation (AS2)</span></span>](../core/configuring-validation-as2.md)  
  
-   [<span data-ttu-id="894a6-115">設定通知 (MDN) (AS2)</span><span class="sxs-lookup"><span data-stu-id="894a6-115">Configuring Acknowledgements (MDNs) (AS2)</span></span>](../core/configuring-acknowledgements-mdns-as2.md)  
  
-   [<span data-ttu-id="894a6-116">設定本機主機設定 (AS2)</span><span class="sxs-lookup"><span data-stu-id="894a6-116">Configuring Local Host Settings (AS2)</span></span>](../core/configuring-local-host-settings-as2.md)  
  
-   [<span data-ttu-id="894a6-117">設定簽章憑證 (AS2)</span><span class="sxs-lookup"><span data-stu-id="894a6-117">Configuring Signature Certificates (AS2)</span></span>](../core/configuring-signature-certificates-as2.md)  
  
-   [<span data-ttu-id="894a6-118">設定傳送埠關聯 (AS2)</span><span class="sxs-lookup"><span data-stu-id="894a6-118">Configuring Send Port Association (AS2)</span></span>](../core/configuring-send-port-association-as2.md)  
  
## <a name="see-also"></a><span data-ttu-id="894a6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="894a6-119">See Also</span></span>  
 [<span data-ttu-id="894a6-120">設定 AS2 屬性</span><span class="sxs-lookup"><span data-stu-id="894a6-120">Configuring AS2 Properties</span></span>](../core/configuring-as2-properties.md)