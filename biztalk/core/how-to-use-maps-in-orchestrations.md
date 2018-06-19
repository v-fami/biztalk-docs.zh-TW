---
title: 如何在協調流程中使用對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dfd628d8-c163-431d-8ad7-d7d77007c549
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e67249857ec00b2ca66648c1985f0c336d93b3b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255326"
---
# <a name="how-to-use-maps-in-orchestrations"></a><span data-ttu-id="fecd8-102">如何在協調流程中使用對應</span><span class="sxs-lookup"><span data-stu-id="fecd8-102">How to Use Maps in Orchestrations</span></span>
<span data-ttu-id="fecd8-103">「BizTalk 對應工具」是在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 環境中執行的工具。</span><span class="sxs-lookup"><span data-stu-id="fecd8-103">BizTalk Mapper is a tool that runs within the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span> <span data-ttu-id="fecd8-104">您可以使用 BizTalk 對應工具建立及編輯對應，並在其中使用連結和運算質定義輸入和輸出結構描述之間的關係。</span><span class="sxs-lookup"><span data-stu-id="fecd8-104">You use BizTalk Mapper to create and edit maps in which you use links and functoids to define the relationship between an input and an output schema.</span></span> <span data-ttu-id="fecd8-105">連結定義記錄或欄位的直接資料複本。</span><span class="sxs-lookup"><span data-stu-id="fecd8-105">A link defines a direct data copy of a record or field.</span></span> <span data-ttu-id="fecd8-106">連結可以直接連接項目到另一個結構描述，也可以建立與運算質的連接。</span><span class="sxs-lookup"><span data-stu-id="fecd8-106">Links may directly connect to items in the other schema, or they may form connections to functoids.</span></span> <span data-ttu-id="fecd8-107">運算質執行更加複雜的資料操作。</span><span class="sxs-lookup"><span data-stu-id="fecd8-107">Functoids perform more complex data manipulations.</span></span>  
  
## <a name="examples-of-using-maps"></a><span data-ttu-id="fecd8-108">對應的使用範例</span><span class="sxs-lookup"><span data-stu-id="fecd8-108">Examples of Using Maps</span></span>  
 <span data-ttu-id="fecd8-109">下列範例顯示對應的一些使用方式：</span><span class="sxs-lookup"><span data-stu-id="fecd8-109">The following samples show ways in which you can use maps:</span></span>  
  
-   [<span data-ttu-id="fecd8-110">XML 工具 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="fecd8-110">XML Tools (BizTalk Server Samples Folder)</span></span>](../core/xml-tools-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="fecd8-111">PartyResolution （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="fecd8-111">PartyResolution (BizTalk Server Sample)</span></span>](../core/partyresolution-biztalk-server-sample.md)  
  
-   <span data-ttu-id="fecd8-112">從下載 SDK 範例 「 使用大量複製運算質 」 [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。</span><span class="sxs-lookup"><span data-stu-id="fecd8-112">Download the SDK sample "Using the Mass Copy Functoid" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
-   <span data-ttu-id="fecd8-113">從下載 SDK 範例 「 使用迴圈運算質 」 [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。</span><span class="sxs-lookup"><span data-stu-id="fecd8-113">Download the SDK sample "Using the Looping Functoid" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
-   <span data-ttu-id="fecd8-114">從下載 SDK 範例 「 對應到重複結構 」 [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。</span><span class="sxs-lookup"><span data-stu-id="fecd8-114">Download the SDK sample "Mapping to a Repeating Structure" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
-   <span data-ttu-id="fecd8-115">從下載 SDK 範例 「 使用表格迴圈運算質 」 [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。</span><span class="sxs-lookup"><span data-stu-id="fecd8-115">Download the SDK sample "Using the Table Looping Functoid" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
-   <span data-ttu-id="fecd8-116">從下載 SDK 範例 「 使用值對應和值對應 （簡維） 運算質 」 [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。</span><span class="sxs-lookup"><span data-stu-id="fecd8-116">Download the SDK sample "Using the Value Mapping and Value Mapping (Flattening) Functoids" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fecd8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fecd8-117">See Also</span></span>  
 <span data-ttu-id="fecd8-118">[使用 BizTalk 對應工具建立對應](../core/creating-maps-using-biztalk-mapper.md) </span><span class="sxs-lookup"><span data-stu-id="fecd8-118">[Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md) </span></span>  
 <span data-ttu-id="fecd8-119">[建構訊息](../core/constructing-messages.md) </span><span class="sxs-lookup"><span data-stu-id="fecd8-119">[Constructing Messages](../core/constructing-messages.md) </span></span>  
 <span data-ttu-id="fecd8-120">[如何設定 「 轉換 」 圖形](../core/how-to-configure-the-transform-shape.md) </span><span class="sxs-lookup"><span data-stu-id="fecd8-120">[How to Configure the Transform Shape](../core/how-to-configure-the-transform-shape.md) </span></span>  
 [<span data-ttu-id="fecd8-121">如何使用運算式動態地轉換訊息</span><span class="sxs-lookup"><span data-stu-id="fecd8-121">How to Use Expressions to Dynamic Transform Messages</span></span>](../core/how-to-use-expressions-to-dynamic-transform-messages.md)