---
title: 結構描述 Validation2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f9d1576-10df-4c5a-9ae0-618f0dd54b4e
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8648b1fc098fc303f3afa2fc47733103f30a6f0a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999465"
---
# <a name="schema-validation"></a><span data-ttu-id="8cb20-102">結構描述驗證</span><span class="sxs-lookup"><span data-stu-id="8cb20-102">Schema Validation</span></span>
<span data-ttu-id="8cb20-103">EDI 接收管線和 EDI 傳送管線會使用下列結構描述驗證訊息：</span><span class="sxs-lookup"><span data-stu-id="8cb20-103">The EDI receive pipeline and EDI send pipeline validate a message using the following schemas:</span></span>  
  
- <span data-ttu-id="8cb20-104">**信封驗證**： 服務結構描述中`Microsoft.BizTalk.Edi.BaseArtifacts.dll`中 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cb20-104">**Envelope validation**: Service schema in `Microsoft.BizTalk.Edi.BaseArtifacts.dll` in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]</span></span>  
  
- <span data-ttu-id="8cb20-105">**交易集驗證**： 結構描述中的訊息結構描述儲存在[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI</span><span class="sxs-lookup"><span data-stu-id="8cb20-105">**Transaction set validation**: Message schemas in the schema store in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI</span></span>  
  
- <span data-ttu-id="8cb20-106">**通知訊息驗證**: CONTRL，contrl、997 和 TA1 結構描述中的`Microsoft.BizTalk.Edi.BaseArtifacts.dll`。</span><span class="sxs-lookup"><span data-stu-id="8cb20-106">**Acknowledgment message validation**: CONTRL, 997, and TA1 schema in `Microsoft.BizTalk.Edi.BaseArtifacts.dll`.</span></span>  
  
  <span data-ttu-id="8cb20-107">中的結構描述`Microsoft.BizTalk.Edi.BaseArtifacts.dll`安裝程式會自動部署。</span><span class="sxs-lookup"><span data-stu-id="8cb20-107">The schemas in `Microsoft.BizTalk.Edi.BaseArtifacts.dll` are automatically deployed by the setup program.</span></span> <span data-ttu-id="8cb20-108">這些結構描述所述**結構描述**節點**BizTalk EDI 應用程式**在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="8cb20-108">These schemas are listed in the **Schemas** node of the **BizTalk EDI Application** in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
  <span data-ttu-id="8cb20-109">若要使用的訊息結構描述，您必須安裝它們在硬碟機，您的伺服器上執行中的 MicrosoftEdiXSDTemplates.exe 自動解壓縮檔案[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI 資料夾，然後將其部署在您專案中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8cb20-109">To use the message schemas, you must install them on the hard drive of your server by executing the MicrosoftEdiXSDTemplates.exe self-extracting file in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI folder, and then deploy them in your project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
  <span data-ttu-id="8cb20-110">**結構描述判斷**</span><span class="sxs-lookup"><span data-stu-id="8cb20-110">**Schema Determination**</span></span>  
  
  <span data-ttu-id="8cb20-111">當 EDI 接收管線處理接收訊息時，它會判斷要用於透過協議尋查和結構描述探索程序處理訊息的結構描述的命名空間。</span><span class="sxs-lookup"><span data-stu-id="8cb20-111">When the EDI receive pipeline processes a receive message, it determines the namespace of the schema to use in processing the message through the agreement lookup and schema discovery process.</span></span> <span data-ttu-id="8cb20-112">如需詳細資訊，請參閱 <<c0> [ 協議解析、 結構描述探索和授權收到 EDI 訊息](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)。</span><span class="sxs-lookup"><span data-stu-id="8cb20-112">For more information, see [Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).</span></span>  
  
  <span data-ttu-id="8cb20-113">當 EDI 傳送管線建立要傳送的訊息時，它會使用協議屬性填入信封，，，然後執行交易集中的 結構描述驗證資訊。</span><span class="sxs-lookup"><span data-stu-id="8cb20-113">When the EDI send pipeline creates a message to send, it uses agreement properties to populate the envelope, and then performs schema validation of the information in the transaction set.</span></span> <span data-ttu-id="8cb20-114">之後載入結構描述，傳送管線會驗證協議屬性 （或後援協議，如果已指定沒有協議） 結構描述。</span><span class="sxs-lookup"><span data-stu-id="8cb20-114">After loading the schema, the send pipeline validates the schema against agreement properties (or fallback agreement if no agreement has been designated).</span></span> <span data-ttu-id="8cb20-115">如果結構描述通過驗證，則管線會對照結構描述驗證交易集。</span><span class="sxs-lookup"><span data-stu-id="8cb20-115">If the schema validates, the pipeline validates the transaction set against the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cb20-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cb20-116">See Also</span></span>  
 [<span data-ttu-id="8cb20-117">EDI 訊息驗證</span><span class="sxs-lookup"><span data-stu-id="8cb20-117">EDI Message Validation</span></span>](../core/edi-message-validation.md)