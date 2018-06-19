---
title: 關於執行個體訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de7fc3d3-57a7-4df9-b981-127e21941e22
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf956fb9f201697ac8c2b7da2135e469e03de55e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224774"
---
# <a name="about-instance-messages"></a><span data-ttu-id="caaec-102">關於執行個體訊息</span><span class="sxs-lookup"><span data-stu-id="caaec-102">About Instance Messages</span></span>
<span data-ttu-id="caaec-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送和接收執行個體訊息，每個執行個體訊息通常都代表一或多個商業文件 (例如訂單)。</span><span class="sxs-lookup"><span data-stu-id="caaec-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends and receives instance messages, each of which typically represents one or more business documents such as a purchase order.</span></span> <span data-ttu-id="caaec-104">執行個體訊息是由一或多個結構描述定義的訊息結構執行個體。</span><span class="sxs-lookup"><span data-stu-id="caaec-104">An instance message is an instance of a message structure defined by one or more schemas.</span></span> <span data-ttu-id="caaec-105">一個結構描述或是一組一起使用的結構描述會定義哪些內容可組成有效的執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="caaec-105">A schema, or a set of schemas being used together, defines what constitutes a valid instance message.</span></span> <span data-ttu-id="caaec-106">例如，訂單可能被定義為在其中有數個記錄，例如 ShipTo 記錄、BillTo 記錄、Items 記錄等等。</span><span class="sxs-lookup"><span data-stu-id="caaec-106">For example, a purchase order might be defined to have several records within it, such as a ShipTo record, a BillTo record, an Items record, and so on.</span></span> <span data-ttu-id="caaec-107">這些記錄的每一個都可以定義為包含自己的子記錄和欄位。</span><span class="sxs-lookup"><span data-stu-id="caaec-107">Each of these records can be defined to contain their own subrecords and fields.</span></span> <span data-ttu-id="caaec-108">對應的結構描述定義這些記錄與欄位的可能內容，對應的執行個體訊息則包含實際的訂單，而這些訂單包含根據結構描述結構化的訂單資料。</span><span class="sxs-lookup"><span data-stu-id="caaec-108">The corresponding schema defines the potential contents of these records and fields and the corresponding instance messages contain actual purchase orders that contain purchase order data structured according to the schema.</span></span>  
  
 <span data-ttu-id="caaec-109">雖然所有的訊息格式都會轉譯成 XML 這種特殊格式以供內部處理，BizTalk Server 仍可使用可延伸的各種格式來傳送和接收執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="caaec-109">BizTalk Server can send and receive instance messages in an extensible variety of formats although one format, XML, has special significance as the format into which all message formats are translated for internal processing.</span></span> <span data-ttu-id="caaec-110">特定的 XML 文件會使用一組定義明確的開始和結束標記，以階層方式排列以便將資料組織在訊息中，並決定某個資料項目結束和另一個資料項目開始的位置。</span><span class="sxs-lookup"><span data-stu-id="caaec-110">A particular XML document uses a well-defined set of starting and ending tags, arranged hierarchically, to organize the data within the message and determine where one data item ends and another begins.</span></span> <span data-ttu-id="caaec-111">一或多個對應的 XML 結構描述會定義在其他標記中允許哪些標記、順序為何，因此可決定符合訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="caaec-111">One or more corresponding XML schemas define which tags are allowed within other tags, in what order, thereby governing the structure of conforming messages.</span></span>  
  
 <span data-ttu-id="caaec-112">另一個廣泛的格式類別 (也稱為一般檔案格式) 則是舊有系統常使用的。</span><span class="sxs-lookup"><span data-stu-id="caaec-112">Another broad category of formats, known as flat file formats, are commonly used by legacy systems.</span></span> <span data-ttu-id="caaec-113">這些格式使用分隔符號 (例如定位元) 及固定長度欄位的組合，來決定某個資料項目結束和另一個資料項目開始的位置。</span><span class="sxs-lookup"><span data-stu-id="caaec-113">These formats use some combination of delimiters (such as tabs) and fixed length fields to determine where one data item ends and another begins.</span></span>  
  
 <span data-ttu-id="caaec-114">本節提供 BizTalk Server 經常處理的兩個訊息類型結構的概要簡介。</span><span class="sxs-lookup"><span data-stu-id="caaec-114">This section provides a high-level overview of the structure of these two types of messages that are commonly handled by BizTalk Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="caaec-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="caaec-115">In This Section</span></span>  
  
-   [<span data-ttu-id="caaec-116">XML 訊息的結構</span><span class="sxs-lookup"><span data-stu-id="caaec-116">Structure of an XML Message</span></span>](../core/structure-of-an-xml-message.md)  
  
-   [<span data-ttu-id="caaec-117">一般檔案訊息的結構</span><span class="sxs-lookup"><span data-stu-id="caaec-117">Structure of a Flat File Message</span></span>](../core/structure-of-a-flat-file-message.md)