---
title: 不同類型的 BizTalk 結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8847d3-6f0e-4982-b4a8-92a5f39a4b48
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 051cd8fb9824cece316ea6f56e318490eacf88c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240278"
---
# <a name="different-types-of-biztalk-schemas"></a><span data-ttu-id="98216-102">不同類型的 BizTalk 結構描述</span><span class="sxs-lookup"><span data-stu-id="98216-102">Different Types of BizTalk Schemas</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="98216-103"> 支援下列四種類型的結構描述：</span><span class="sxs-lookup"><span data-stu-id="98216-103"> supports the following four types of schemas:</span></span>  
  
-   <span data-ttu-id="98216-104">**XML 結構描述**。</span><span class="sxs-lookup"><span data-stu-id="98216-104">**XML schema**.</span></span> <span data-ttu-id="98216-105">XML 結構描述定義 XML 執行個體訊息類別的結構。</span><span class="sxs-lookup"><span data-stu-id="98216-105">An XML schema defines the structure of a class of XML instance messages.</span></span> <span data-ttu-id="98216-106">由於這種類型的結構描述是使用 XML 結構描述定義 (XSD) 語言定義 XML 執行個體訊息的結構，而這正是 XSD 的用途，所以這類結構描述會以直接的方式使用 XSD。</span><span class="sxs-lookup"><span data-stu-id="98216-106">Because this type of schema uses XML Schema definition (XSD) language to define the structure of an XML instance message, and this is the intended purpose of XSD, such schemas use XSD in a straightforward way.</span></span>  
  
-   <span data-ttu-id="98216-107">**一般檔案結構描述**。</span><span class="sxs-lookup"><span data-stu-id="98216-107">**Flat file schema**.</span></span> <span data-ttu-id="98216-108">一般檔案結構描述是用來定義使用一般檔案格式 (分隔或位置或這兩者的組合) 的執行個體訊息類別之結構。</span><span class="sxs-lookup"><span data-stu-id="98216-108">A flat file schema defines the structure of a class of instance messages that use a flat file format, either delimited or positional or some combination thereof.</span></span> <span data-ttu-id="98216-109">由於 XSD 的原生語意功能無法滿足定義一般檔案執行個體訊息結構的所有需求 (例如可用於一般檔案中不同記錄和欄位的各種分隔符號)，因此，BizTalk Server 使用了 XSD 的註解功能，將此額外資訊儲存在 XSD 結構描述中。</span><span class="sxs-lookup"><span data-stu-id="98216-109">Because the native semantic capabilities of XSD do not accommodate all of the requirements for defining the structure of flat file instance messages—such as the various types of delimiters that might be used for different records and fields within the flat file—BizTalk Server uses the annotation capabilities of XSD to store this extra information within an XSD schema.</span></span> <span data-ttu-id="98216-110">BizTalk Server 定義了一組豐富的特定註解標記，可用來儲存所有必要的額外資訊。</span><span class="sxs-lookup"><span data-stu-id="98216-110">BizTalk Server defines a rich set of specific annotation tags that can be used to store all of the required additional information.</span></span>  
  
-   <span data-ttu-id="98216-111">**信封結構描述**。</span><span class="sxs-lookup"><span data-stu-id="98216-111">**Envelope schema**.</span></span> <span data-ttu-id="98216-112">信封結構描述是特殊類型的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="98216-112">An envelope schema is a special type of XML schema.</span></span> <span data-ttu-id="98216-113">信封結構描述是用來定義 XML 信封的結構，可用來將一或多個 XML 商務文件包裝成單一 XML 執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="98216-113">Envelope schemas are used to define the structure of XML envelopes, which are used to wrap one or more XML business documents into a single XML instance message.</span></span> <span data-ttu-id="98216-114">將 XML 結構描述定義為信封結構描述時，根據信封結構描述中是否定義了一個以上的根記錄而定，會需要一些其他的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="98216-114">When you define an XML schema to be an envelope schema, a couple of additional property settings are required, depending on such factors as whether there are more than one root record defined in the envelope schema.</span></span>  
  
-   <span data-ttu-id="98216-115">**屬性結構描述**。</span><span class="sxs-lookup"><span data-stu-id="98216-115">**Property schema**.</span></span> <span data-ttu-id="98216-116">屬性結構描述是與 BizTalk Server 中所具有的兩種機制之一搭配使用，該種機制稱之為屬性升級。</span><span class="sxs-lookup"><span data-stu-id="98216-116">A property schema is used with one of the two mechanisms that exist within BizTalk Server for what is known as property promotion.</span></span> <span data-ttu-id="98216-117">屬性升級是將執行個體訊息內的特定值複製到訊息內容的程序。</span><span class="sxs-lookup"><span data-stu-id="98216-117">Property promotion is the process of copying specific values from deep within an instance message to the message context.</span></span> <span data-ttu-id="98216-118">透過訊息內容，這些值可以更容易被各種 BizTalk Server 元件存取。</span><span class="sxs-lookup"><span data-stu-id="98216-118">From the message context, these values are more easily accessed by various BizTalk Server components.</span></span> <span data-ttu-id="98216-119">這些元件可使用這些值來執行訊息路由等動作。</span><span class="sxs-lookup"><span data-stu-id="98216-119">These components use the values to perform actions such as message routing.</span></span> <span data-ttu-id="98216-120">您也可以依相反方向複製升級的屬性值 (從較容易存取的訊息內容複製回執行個體訊息內)，只要是在執行個體訊息傳送到目的地之前即可。</span><span class="sxs-lookup"><span data-stu-id="98216-120">Promoted property values can also be copied in the other direction, from the more easily accessible message context back into the depths of the instance message, just before the instance message is sent to its destination.</span></span> <span data-ttu-id="98216-121">屬性結構描述是 BizTalk 結構描述的簡單版本，在執行個體訊息與訊息內容之間來回複製升級屬性的過程中會使用到。</span><span class="sxs-lookup"><span data-stu-id="98216-121">A property schema is a simple version of a BizTalk schema that plays a role in the process of copying promoted properties back and forth between the instance message and the message context.</span></span>  
  
 <span data-ttu-id="98216-122">本節其餘部分會提供有關 BizTalk Server 中這四種類型的結構描述之詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="98216-122">The remainder of section provides additional information about these four types of schemas in BizTalk Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="98216-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="98216-123">In This Section</span></span>  
  
-   [<span data-ttu-id="98216-124">XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="98216-124">XML Schemas</span></span>](../core/xml-schemas.md)  
  
-   [<span data-ttu-id="98216-125">一般檔案結構描述</span><span class="sxs-lookup"><span data-stu-id="98216-125">Flat File Schemas</span></span>](../core/flat-file-schemas.md)  
  
-   [<span data-ttu-id="98216-126">信封結構描述</span><span class="sxs-lookup"><span data-stu-id="98216-126">Envelope Schemas</span></span>](../core/envelope-schemas.md)  
  
-   [<span data-ttu-id="98216-127">屬性結構描述</span><span class="sxs-lookup"><span data-stu-id="98216-127">Property Schemas</span></span>](../core/property-schemas.md)