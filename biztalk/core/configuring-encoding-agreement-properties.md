---
title: 設定編碼協議屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.admin.ediagreement.properties
ms.assetid: 0cb1146e-177c-42fa-b1d8-a834229c2af9
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cde69b1514b2e376a7df415befc0a686300009f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233926"
---
# <a name="configuring-encoding-agreement-properties"></a><span data-ttu-id="902b2-102">設定編碼協議屬性</span><span class="sxs-lookup"><span data-stu-id="902b2-102">Configuring Encoding Agreement Properties</span></span>
<span data-ttu-id="902b2-103">交易夥伴協議 (TPA) 是兩個交易夥伴之間透過特定 B2B 通訊協定交易訊息時所採用的決定性與繫結性協議。</span><span class="sxs-lookup"><span data-stu-id="902b2-103">A Trading Partner Agreement (TPA) is a definitive and binding agreement between two trading partners for transacting messages over a specific B2B Protocol.</span></span> <span data-ttu-id="902b2-104">簡單地說，TPA 指的是當兩個商務設定檔互相交換 B2B 訊息時，對於使用特定訊息編碼通訊協定 (X12 或 EDIFACT) 或特定傳輸通訊協定 (AS2) 的一種共識。</span><span class="sxs-lookup"><span data-stu-id="902b2-104">In simpler terms, a TPA is an understanding between two business profiles to use a specific message encoding protocol (X12 or EDIFACT) or a specific transport protocol (AS2) while exchanging B2B messages with each other.</span></span> <span data-ttu-id="902b2-105">除了用來對於使用一致的編碼與傳輸通訊協議達成共識之外，協議還可以用來自訂訊息的格式與傳遞方式。</span><span class="sxs-lookup"><span data-stu-id="902b2-105">In addition to agreeing upon the encoding and transport protocol, an agreement can be used to customize how the messages will be formed and delivered.</span></span>  
  
-   <span data-ttu-id="902b2-106">在編碼通訊協定設定當中，您還可以定義傳送者是否預期收到通知 (不管訊息是以批次還是個別方式傳送)。</span><span class="sxs-lookup"><span data-stu-id="902b2-106">As part of the encoding protocol settings, you can also define whether the sending party expects an acknowledgement, whether the messages will be batched or sent individually, etc.</span></span>  
  
-   <span data-ttu-id="902b2-107">在傳輸通訊協定設定當中，您還可以定義訊息是否應該經過簽章、加密等等。</span><span class="sxs-lookup"><span data-stu-id="902b2-107">As part of the transport protocol settings, you can also define whether the message should be signed, whether the message should be encrypted, etc.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="902b2-108">如需傳輸通訊協定 (AS2) 設定的詳細資訊，請參閱[設定 AS2 協議屬性](../core/configuring-as2-agreement-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="902b2-108">For more information about transport protocol (AS2) settings, see [Configuring AS2 Agreement Properties](../core/configuring-as2-agreement-properties.md).</span></span>  
  
 <span data-ttu-id="902b2-109">建立協議時，您必須考量下列事項：</span><span class="sxs-lookup"><span data-stu-id="902b2-109">You must make the following considerations while creating an agreement:</span></span>  
  
-   <span data-ttu-id="902b2-110">兩個合作對象之間的交易夥伴協議為雙向協議。</span><span class="sxs-lookup"><span data-stu-id="902b2-110">A trading partner agreement between two parties is bi-directional.</span></span> <span data-ttu-id="902b2-111">兩個合作對象 (Party A 與 Party B) 之間的單一協議可讓 Party A 傳送訊息給 Party B，且 Party A 亦可接收來自 Party B 的訊息。為了在使用者介面中呈現雙向協議，每個單向協議各以一個索引標籤來代表。因此，您也可以在協議使用者介面中，您會看到兩個索引標籤， **party a-> [partyb]** （代表單向協議的訊息會從合作對象 A 傳送至合作對象 B） 和 **[partyb]-> party a** (代表單向協議從 Party b 傳送至 party a 的訊息。）</span><span class="sxs-lookup"><span data-stu-id="902b2-111">A single agreement between two parties (Party A and Party B) can be used to send messages from Party A to Party B and also to receive messages from Party B to Party A. To represent a bi-directional agreement in the user interface, each one-way agreement is represented in a single tab. So, in the agreement user interface, you will see two tabs, **PartyA->PartyB** (representing the one-way agreement for messages sent from Party A to Party B) and **PartyB->PartyA** (representing the one-way agreement for messages sent from PartyB to PartyA.)</span></span>  
  
-   <span data-ttu-id="902b2-112">每個單向協議皆代表一個端對端訊息交易。</span><span class="sxs-lookup"><span data-stu-id="902b2-112">Each one-way agreement caters to one end-to-end message transaction.</span></span> <span data-ttu-id="902b2-113">另外，傳送或接收通知亦為同一個訊息交易的一部份，因此應該在同一個單向協議索引標籤上設定。例如，假設 Party A 傳送 EDI 交換給 Party B 以及回應，合作對象 B 通知傳回給合作對象 a。因此，與傳送交換並預期收到通知相關的所有屬性必須都設定**party a-> partyb**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="902b2-113">Sending or receiving acknowledgements is also part of the same message transaction and hence should be configured on the same one-way agreement tab. For example, consider Party A sends an EDI interchange to Party B and in response, Party B sends an acknowledgement back to Party A. So, all the properties related to sending an interchange and expecting an acknowledgement must be set on the **PartyA->PartyB** tab.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="902b2-114">雖然通知屬於同一個訊息交易時，應如何產生通知相關的屬性中所設定**partyb-> party a**  索引標籤。這是必要的因為通知內容屬性為傳送者和接收者辨識符號都會設定為您在指定的值相反**party a-> partyb**  索引標籤。例如，如果在交換訊息所解析成的協議中，傳送者與接收者識別碼是設為 THEM 與 US，則通知裡的傳送者與接收者內容屬性將設為 US 與 THEM。</span><span class="sxs-lookup"><span data-stu-id="902b2-114">Even though the acknowledgement is part of the same message transaction, the properties related to how the acknowledgement should be generated are configured in the **PartyB->PartyA** tab. This is required because the acknowledgement context properties for the sender and receiver qualifiers are set to the opposite of the values you specified in the **PartyA->PartyB** tab. For example, if sender and receiver identifiers are set to THEM and US in the agreement to which the interchange message resolved to, the sender and receiver context properties will be set to US and THEM in the acknowledgement.</span></span> <span data-ttu-id="902b2-115">一般而言，其他單向協議索引標籤也會分別將傳送者與接收者識別項設定為 US 與 THEM。</span><span class="sxs-lookup"><span data-stu-id="902b2-115">Typically, the other one-way agreement tab would also have the sender and receiver identifiers set to US and THEM respectively.</span></span> <span data-ttu-id="902b2-116">因此，通知訊息會解析成該協議，並將挑選屬性設定。</span><span class="sxs-lookup"><span data-stu-id="902b2-116">Hence, the acknowledgement message would resolve to that agreement and the properties setting will be picked.</span></span> <span data-ttu-id="902b2-117">因此，如果您想要讓通知使用不同的項目分隔符號，或是如果您想要讓通知使用 CR LF 中, 指定內容**partyb-> party a**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="902b2-117">So, if you want to have the acknowledgement to use different element separators or if you want to have the acknowledgement to use CR LF, specify the properties in the **PartyB->PartyA** tab.</span></span>  
    >   
    >  <span data-ttu-id="902b2-118">在概念上，將會從傳送者與接收者辨識符號與在通知的內容屬性中所設定值相同的任一個單向協議索引標籤中挑選通知的屬性。</span><span class="sxs-lookup"><span data-stu-id="902b2-118">Conceptually, the properties for the acknowledgement will be picked from any one-way agreement tab that has the same sender and receiver qualifiers as set in the acknowledgement’s context properties.</span></span> <span data-ttu-id="902b2-119">但為便於實際應用，通常會在您所建立由交換解析而成之協議的其他單向協議索引標籤中設定此屬性。</span><span class="sxs-lookup"><span data-stu-id="902b2-119">However, for ease of practical use, you would typically set this in the other one-way agreement tab of the agreement that you created to which the interchange would have resolved.</span></span>  
  
-   <span data-ttu-id="902b2-120">您可以擁有一個編碼協議 (以定義訊息使用的訊息編碼) 與一個傳輸協議 (以定義交換訊息時使用的傳輸通訊協定)。</span><span class="sxs-lookup"><span data-stu-id="902b2-120">You can have an encoding agreement (to define the message encoding to be used for the messages) and a transport agreement (to define the transport protocol to be used for exchanging messages).</span></span> <span data-ttu-id="902b2-121">您必須擁有編碼協議。</span><span class="sxs-lookup"><span data-stu-id="902b2-121">Having an encoding agreement is mandatory.</span></span> <span data-ttu-id="902b2-122">如果兩個合作對象都要使用 AS2 通訊協定來傳輸訊息，可以選擇僅擁有 AS2 協議。</span><span class="sxs-lookup"><span data-stu-id="902b2-122">The parties may choose to have an AS2 agreement only if they want to use the AS2 protocol to transfer messages.</span></span> <span data-ttu-id="902b2-123">例如，如果兩個合作對象選擇透過電子郵件來傳輸訊息，則不需要 AS2 協議。</span><span class="sxs-lookup"><span data-stu-id="902b2-123">For example, an AS2 agreement is not required if the two parties choose to transfer messages over e-mail.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="902b2-124">如需有關 AS2 協議的詳細資訊，請參閱[設定 AS2 協議屬性](../core/configuring-as2-agreement-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="902b2-124">For more information about AS2 agreement, see [Configuring AS2 Agreement Properties](../core/configuring-as2-agreement-properties.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="902b2-125">本節內容</span><span class="sxs-lookup"><span data-stu-id="902b2-125">In This Section</span></span>  
  
-   [<span data-ttu-id="902b2-126">設定 X12 特有協議屬性</span><span class="sxs-lookup"><span data-stu-id="902b2-126">Configuring X12-Specific Agreement Properties</span></span>](../core/configuring-x12-specific-agreement-properties.md)  
  
-   [<span data-ttu-id="902b2-127">設定 EDIFACT 特定協議屬性</span><span class="sxs-lookup"><span data-stu-id="902b2-127">Configuring EDIFACT-Specific Agreement Properties</span></span>](../core/configuring-edifact-specific-agreement-properties.md)