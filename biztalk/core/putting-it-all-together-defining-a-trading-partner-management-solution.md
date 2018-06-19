---
title: 整合在一起： 定義交易夥伴管理解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4219312a-c4b5-45f3-b77b-d5cc4f1a1ca4
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea32fba8e9e57d7a0549a680b06e08d5bf8e087f
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "22269222"
---
# <a name="putting-it-all-together-defining-a-trading-partner-management-solution"></a><span data-ttu-id="6412c-102">整合在一起： 定義交易夥伴管理解決方案</span><span class="sxs-lookup"><span data-stu-id="6412c-102">Putting it all Together: Defining a Trading Partner Management Solution</span></span>
<span data-ttu-id="6412c-103">在瞭解用來建立 TPM 方案的不同元件類型後，接著要介紹典型的 TPM 方案流程，以及如何合併使用不同的建置組塊。</span><span class="sxs-lookup"><span data-stu-id="6412c-103">Now that we have understood about the different types of components in building a TPM solution, let us understand the flow of a typical TPM solution and how the different building blocks work together.</span></span> <span data-ttu-id="6412c-104">本節也列示建立 TPM 方案模型的一些最佳做法。</span><span class="sxs-lookup"><span data-stu-id="6412c-104">This section also lists some best practices for modeling a TPM solution.</span></span>  
  
 <span data-ttu-id="6412c-105">建立 TPM 方案的典型流程包含以下各項：</span><span class="sxs-lookup"><span data-stu-id="6412c-105">A typical flow for creating a TPM solution would include the following:</span></span>  
  
1.  <span data-ttu-id="6412c-106">建立代表商務交易中之所有相關組織的夥伴。</span><span class="sxs-lookup"><span data-stu-id="6412c-106">Create partners representing all the organizations involved in a business trade.</span></span> <span data-ttu-id="6412c-107">例如，如果有兩個商業組織和商務交易有關，必須為每個組織建立一個交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="6412c-107">For example, if there are two business organizations involved in a business trade, you must create a trading partner for each of them.</span></span> <span data-ttu-id="6412c-108">如需有關如何建立交易夥伴的指示，請參閱[設定一般合作對象屬性](../core/configuring-general-party-properties.md)或[設定一般合作對象屬性 (AS2)](../core/configuring-general-party-properties-as2.md)</span><span class="sxs-lookup"><span data-stu-id="6412c-108">For instructions on how to create trading partners, see [Configuring General Party Properties](../core/configuring-general-party-properties.md) or [Configuring General Party Properties (AS2)](../core/configuring-general-party-properties-as2.md)</span></span>  
  
2.  <span data-ttu-id="6412c-109">對於組織內的每個業務部門，在夥伴中建立代表業務部門的設定檔。</span><span class="sxs-lookup"><span data-stu-id="6412c-109">For each business division within an organization, create a profile within the partner representing the business division.</span></span> <span data-ttu-id="6412c-110">例如，如果組織包含「採購」和「供應」業務部門，必須在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中各以一個商務設定檔分別代表每個部門。</span><span class="sxs-lookup"><span data-stu-id="6412c-110">For example, if an organization has “Purchase” and “Supplies” business divisions, each of these divisions must be represented as a business profile in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="6412c-111">另外，除了為代表您組織的夥伴建立商務設定檔之外，也必須為與您交易的夥伴建立商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="6412c-111">Also, you must create the business profiles not just for the partner representing your organization but also the partner with which you trade.</span></span> <span data-ttu-id="6412c-112">如需有關如何建立商務設定檔的指示，請參閱[設定商務設定檔屬性](../core/configuring-business-profile-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6412c-112">For instructions on how to create business profiles, see [Configuring Business Profile Properties](../core/configuring-business-profile-properties.md).</span></span>  
  
3.  <span data-ttu-id="6412c-113">為每個商務設定檔定義 B2B 通訊協定設定 (含訊息編碼設定與訊息通訊協定設定)。</span><span class="sxs-lookup"><span data-stu-id="6412c-113">For each business profile, define the B2B protocol settings that include the message encoding setting and the message protocol settings.</span></span> <span data-ttu-id="6412c-114">這些設定定義 B2B 訊息如何編碼，以及如何在兩個商務設定檔之間傳輸。</span><span class="sxs-lookup"><span data-stu-id="6412c-114">These settings define how the B2B messages are encoded and transported between two business profiles.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6412c-115">在此階段中，指定通訊協定設定是可省略的。</span><span class="sxs-lookup"><span data-stu-id="6412c-115">Specifying protocol settings is optional at this stage.</span></span> <span data-ttu-id="6412c-116">您可以直接在交易夥伴協議中新增通訊協定設定。</span><span class="sxs-lookup"><span data-stu-id="6412c-116">You can directly add the protocol settings as part of the trading partner agreement.</span></span>  
  
4.  <span data-ttu-id="6412c-117">建立商務設定檔之間的交易夥伴協議 (TPA)，此協議定義兩個商務設定檔交換訊息時同意使用的編碼和/或訊息通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6412c-117">Create Trading Partner Agreements (TPA) between the business profiles that define the encoding and/or messaging protocols the two business profiles agree to use while exchanging messages.</span></span> <span data-ttu-id="6412c-118">如需有關如何建立協議的指示，請參閱[設定 X12 特有協議屬性](../core/configuring-x12-specific-agreement-properties.md)，[設定 EDIFACT 特定協議屬性](../core/configuring-edifact-specific-agreement-properties.md)，或[設定 AS2協議屬性](../core/configuring-as2-agreement-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6412c-118">For instructions on how to create agreements, see [Configuring X12-Specific Agreement Properties](../core/configuring-x12-specific-agreement-properties.md), [Configuring EDIFACT-Specific Agreement Properties](../core/configuring-edifact-specific-agreement-properties.md), or [Configuring AS2 Agreement Properties](../core/configuring-as2-agreement-properties.md).</span></span>  
  
 <span data-ttu-id="6412c-119">執行上述工作集合，您會建立與交易夥伴交換 B2B 訊息的 TPM 方案。</span><span class="sxs-lookup"><span data-stu-id="6412c-119">By performing the above set of tasks you would have created TPM solution to exchange B2B messages with your trading partner.</span></span>  
  
## <a name="where-do-i-start"></a><span data-ttu-id="6412c-120">要從何處著手？</span><span class="sxs-lookup"><span data-stu-id="6412c-120">Where do I Start?</span></span>  
 <span data-ttu-id="6412c-121">您可透過下列各節開始進行：</span><span class="sxs-lookup"><span data-stu-id="6412c-121">You can start by going through the following sections:</span></span>  
  
-   <span data-ttu-id="6412c-122">X12 特定教學課程[教學課程 2: EDI 介面開發人員教學課程](../core/tutorial-2-edi-interface-developer-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="6412c-122">X12-specific tutorial at [Tutorial 2: EDI Interface Developer Tutorial](../core/tutorial-2-edi-interface-developer-tutorial.md).</span></span>  
  
-   <span data-ttu-id="6412c-123">AS2 特定教學課程[教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="6412c-123">AS2-specific tutorial at [Tutorial 3: AS2 Tutorial](../core/tutorial-3-as2-tutorial.md).</span></span>  
  
-   <span data-ttu-id="6412c-124">X12-和 EDIFACT-底下的特定逐步解說[開發和設定 BizTalk Server EDI 方案](../core/developing-and-configuring-biztalk-server-edi-solutions.md)。</span><span class="sxs-lookup"><span data-stu-id="6412c-124">X12- and EDIFACT-specific walkthroughs under [Developing and Configuring BizTalk Server EDI Solutions](../core/developing-and-configuring-biztalk-server-edi-solutions.md).</span></span>  
  
-   <span data-ttu-id="6412c-125">底下的 AS2 特定逐步解說[開發和設定 BizTalk Server AS2 解決方案](../core/developing-and-configuring-biztalk-server-as2-solutions.md)。</span><span class="sxs-lookup"><span data-stu-id="6412c-125">AS2-specific walkthroughs under [Developing and Configuring BizTalk Server AS2 Solutions](../core/developing-and-configuring-biztalk-server-as2-solutions.md).</span></span>  
  
-   <span data-ttu-id="6412c-126">建立合作對象、 設定檔和協議的 X12 和 EDIFACT 傳訊依照指示在[設定 EDI 屬性](../core/configuring-edi-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6412c-126">Create parties, profiles, and agreements for X12 and EDIFACT messaging by following instructions at [Configuring EDI Properties](../core/configuring-edi-properties.md).</span></span>  
  
-   <span data-ttu-id="6412c-127">建立合作對象、 設定檔，並依照指示在訊息的 AS2 合約[設定 AS2 屬性](../core/configuring-as2-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6412c-127">Create parties, profiles, and agreements for AS2 messaging by following instructions at [Configuring AS2 Properties](../core/configuring-as2-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6412c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6412c-128">See Also</span></span>  
 [<span data-ttu-id="6412c-129">交易夥伴管理解決方案的建置區塊</span><span class="sxs-lookup"><span data-stu-id="6412c-129">Building Blocks of a Trading Partner Management Solution</span></span>](../core/building-blocks-of-a-trading-partner-management-solution.md)