---
title: 結構描述 Validation2 |Microsoft 文件
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
ms.openlocfilehash: 317fa8e0e5e557993922bba383ebf5eca460fa69
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269238"
---
# <a name="schema-validation"></a><span data-ttu-id="9947d-102">結構描述驗證</span><span class="sxs-lookup"><span data-stu-id="9947d-102">Schema Validation</span></span>
<span data-ttu-id="9947d-103">EDI 接收管線和 EDI 傳送管線會使用下列結構描述驗證訊息：</span><span class="sxs-lookup"><span data-stu-id="9947d-103">The EDI receive pipeline and EDI send pipeline validate a message using the following schemas:</span></span>  
  
-   <span data-ttu-id="9947d-104">**信封驗證**： 服務結構描述中`Microsoft.BizTalk.Edi.BaseArtifacts.dll`中[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9947d-104">**Envelope validation**: Service schema in `Microsoft.BizTalk.Edi.BaseArtifacts.dll` in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]</span></span>  
  
-   <span data-ttu-id="9947d-105">**交易集驗證**： 結構描述中的訊息結構描述儲存在[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI</span><span class="sxs-lookup"><span data-stu-id="9947d-105">**Transaction set validation**: Message schemas in the schema store in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI</span></span>  
  
-   <span data-ttu-id="9947d-106">**通知訊息驗證**: CONTRL、 997 和 TA1 結構描述中的`Microsoft.BizTalk.Edi.BaseArtifacts.dll`。</span><span class="sxs-lookup"><span data-stu-id="9947d-106">**Acknowledgment message validation**: CONTRL, 997, and TA1 schema in `Microsoft.BizTalk.Edi.BaseArtifacts.dll`.</span></span>  
  
 <span data-ttu-id="9947d-107">中的結構描述`Microsoft.BizTalk.Edi.BaseArtifacts.dll`安裝程式會自動部署。</span><span class="sxs-lookup"><span data-stu-id="9947d-107">The schemas in `Microsoft.BizTalk.Edi.BaseArtifacts.dll` are automatically deployed by the setup program.</span></span> <span data-ttu-id="9947d-108">這些結構描述中所列**結構描述**節點**BizTalk EDI 應用程式**中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="9947d-108">These schemas are listed in the **Schemas** node of the **BizTalk EDI Application** in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="9947d-109">若要使用的訊息結構描述，您必須安裝它們在您的伺服器的硬碟機上執行中的 MicrosoftEdiXSDTemplates.exe 自動解壓縮檔案[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI 資料夾，然後將其部署專案中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9947d-109">To use the message schemas, you must install them on the hard drive of your server by executing the MicrosoftEdiXSDTemplates.exe self-extracting file in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI folder, and then deploy them in your project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9947d-110">**結構描述判斷**</span><span class="sxs-lookup"><span data-stu-id="9947d-110">**Schema Determination**</span></span>  
  
 <span data-ttu-id="9947d-111">當 EDI 接收管線處理接收訊息時，它會判斷要用於透過協議尋查和結構描述探索程序處理訊息的結構描述的命名空間。</span><span class="sxs-lookup"><span data-stu-id="9947d-111">When the EDI receive pipeline processes a receive message, it determines the namespace of the schema to use in processing the message through the agreement lookup and schema discovery process.</span></span> <span data-ttu-id="9947d-112">如需詳細資訊，請參閱[協議解析、 結構描述探索和授權接收 EDI 訊息](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)。</span><span class="sxs-lookup"><span data-stu-id="9947d-112">For more information, see [Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).</span></span>  
  
 <span data-ttu-id="9947d-113">當 EDI 傳送管線建立要傳送的訊息時，它會使用協議屬性填入信封，，並接著執行結構描述驗證資訊的交易集內。</span><span class="sxs-lookup"><span data-stu-id="9947d-113">When the EDI send pipeline creates a message to send, it uses agreement properties to populate the envelope, and then performs schema validation of the information in the transaction set.</span></span> <span data-ttu-id="9947d-114">之後載入結構描述，傳送管線會驗證協議屬性 （或後援協議，如果已指定沒有協議） 結構描述。</span><span class="sxs-lookup"><span data-stu-id="9947d-114">After loading the schema, the send pipeline validates the schema against agreement properties (or fallback agreement if no agreement has been designated).</span></span> <span data-ttu-id="9947d-115">如果結構描述通過驗證，則管線會對照結構描述驗證交易集。</span><span class="sxs-lookup"><span data-stu-id="9947d-115">If the schema validates, the pipeline validates the transaction set against the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9947d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9947d-116">See Also</span></span>  
 [<span data-ttu-id="9947d-117">EDI 訊息驗證</span><span class="sxs-lookup"><span data-stu-id="9947d-117">EDI Message Validation</span></span>](../core/edi-message-validation.md)