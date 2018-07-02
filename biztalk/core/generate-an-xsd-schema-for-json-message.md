---
title: 產生 JSON 訊息的 XSD 結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5453b76c-b282-442f-9eb1-6c2628b38ad5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b95af2f3a44454aa59138cd6f77b7f7195cbb02b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971135"
---
# <a name="generate-an-xsd-schema-for-json-message"></a><span data-ttu-id="51e41-102">產生 JSON 訊息的 XSD 結構描述</span><span class="sxs-lookup"><span data-stu-id="51e41-102">Generate an XSD schema for JSON message</span></span>
> [!NOTE]
>  <span data-ttu-id="51e41-103">本教學課程僅適用於 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="51e41-103">This tutorial applies to BizTalk Server only.</span></span>  
  
 <span data-ttu-id="51e41-104">在此解決方案中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式接收 JSON 訊息。</span><span class="sxs-lookup"><span data-stu-id="51e41-104">In this solution, a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application receives a JSON message.</span></span> <span data-ttu-id="51e41-105">應用程式可以處理訊息之前，它必須轉換成 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="51e41-105">Before the application can process the message, it must be converted to an XSD schema.</span></span> <span data-ttu-id="51e41-106">若要這樣做，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]所提供的 JSON 結構描述精靈建立 XSD 結構描述從 JSON 訊息。</span><span class="sxs-lookup"><span data-stu-id="51e41-106">To do so, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides a JSON Schema Wizard that creates an XSD schema from a JSON message.</span></span>  
  
1. <span data-ttu-id="51e41-107">在 Visual Studio 中，建立新[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="51e41-107">In Visual Studio, create a new [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span>  
  
2. <span data-ttu-id="51e41-108">在 [方案總管] 中，以滑鼠右鍵按一下專案名稱 >**新增** > **新項目** > **JSON 結構描述精靈**。</span><span class="sxs-lookup"><span data-stu-id="51e41-108">In the Solution Explorer, right-click the project name > **Add** > **New Item** > **JSON Schema Wizard**.</span></span> <span data-ttu-id="51e41-109">提供的結構描述的名稱 (`PO.xsd`)，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="51e41-109">Provide a name for the schema (`PO.xsd`), and then click **Add**.</span></span>  
  
3. <span data-ttu-id="51e41-110">在 JSON 結構描述精靈中，在 歡迎使用 頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="51e41-110">In the JSON Schema Wizard, on the welcome page, click **Next**.</span></span>  
  
4. <span data-ttu-id="51e41-111">在 [JSON 結構描述資訊] 頁面中，會提供傳送至 JSON 採購訂單檔案的位置[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="51e41-111">In the JSON Schema Information page, provide the location of the JSON purchase order file that is sent to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span> <span data-ttu-id="51e41-112">提供根節點名稱，而目標命名空間，然後按**完成**。</span><span class="sxs-lookup"><span data-stu-id="51e41-112">Provide a root node name, a target namespace, and then click **Finish**.</span></span>  
  
    <span data-ttu-id="51e41-113">![產生的 XSD 結構描述 json](../core/media/btsjson-wizard.png "BTSJSON_Wizard")</span><span class="sxs-lookup"><span data-stu-id="51e41-113">![Generated XSD schema for JSON](../core/media/btsjson-wizard.png "BTSJSON_Wizard")</span></span>  
  
5. <span data-ttu-id="51e41-114">具有指定名稱的結構描述新增至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="51e41-114">A schema with the specified name is added to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="51e41-115">產生的結構描述檔案 (**PO.xsd**) 也會提供範例。</span><span class="sxs-lookup"><span data-stu-id="51e41-115">The generated schema file (**PO.xsd**) is also provided with the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51e41-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51e41-116">See Also</span></span>  
 [<span data-ttu-id="51e41-117">使用 BizTalk Server 處理 JSON 訊息</span><span class="sxs-lookup"><span data-stu-id="51e41-117">Processing JSON messages using BizTalk Server</span></span>](../core/processing-json-messages-using-biztalk-server.md)