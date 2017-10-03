---
title: "限制字元範圍 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e12213bf-750e-43a2-998a-949fa4255b73
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74f1399aaa828d5c23c2600ebabeb7063a982447
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="restricted-character-ranges"></a><span data-ttu-id="223e8-102">限制的字元範圍</span><span class="sxs-lookup"><span data-stu-id="223e8-102">Restricted Character Ranges</span></span>

## <a name="overview"></a><span data-ttu-id="223e8-103">概觀</span><span class="sxs-lookup"><span data-stu-id="223e8-103">Overview</span></span>
<span data-ttu-id="223e8-104">建立一般檔案訊息的結構描述時，您可以指示 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 封鎖特定字元或某範圍的字元，使它們不會包含在任何外寄訊息中。</span><span class="sxs-lookup"><span data-stu-id="223e8-104">When creating a schema for flat file messages, you can direct [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to block a particular character or a range of characters from being included in any outgoing message.</span></span> <span data-ttu-id="223e8-105">若要這麼做，請在 BizTalk 編輯器中，開啟將用來做為目的結構描述的結構描述。</span><span class="sxs-lookup"><span data-stu-id="223e8-105">To do this, in BizTalk Editor, open a schema that is to be used as a destination schema.</span></span> <span data-ttu-id="223e8-106">選取**結構描述**節點並使用**限制的字元**屬性可開啟**限制的字元** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="223e8-106">Select the **Schema** node and the use the **Restricted Characters** property to open the **Restricted Characters** dialog box.</span></span> <span data-ttu-id="223e8-107">輸入範圍，您想要在 BizTalk Server 傳送任何訊息中包含的字元，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="223e8-107">Enter the character range(s) that you want to prevent being included in any message sent by BizTalk Server, and then click **OK**.</span></span> <span data-ttu-id="223e8-108">每當 BizTalk Server 嘗試處理中指定的字元**限制的字元**處理停駐點和錯誤訊息的目的地結構描述 對話方塊就會產生。</span><span class="sxs-lookup"><span data-stu-id="223e8-108">Whenever BizTalk Server attempts to process a character specified in the **Restricted Characters** dialog box of a destination schema, processing stops and an error message is generated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="223e8-109">在 BizTalk Server 中，字元範圍限制是「一般檔案延伸模組」的函式，因此不適用於 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="223e8-109">In BizTalk Server, character range restriction is a function of the Flat File Extension, and as such, does not apply to XML messages.</span></span> <span data-ttu-id="223e8-110">未來為不同類型的訊息所提供的延伸模組之間，可能在它們如何為其支援的訊息格式實作字元範圍限制的方面有所差異。</span><span class="sxs-lookup"><span data-stu-id="223e8-110">Extensions that might be offered in the future for different types of messages might differ in how they implement character range restriction for their supported message formats.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="223e8-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="223e8-111">See Also</span></span>  
-  [<span data-ttu-id="223e8-112">考量當建立一般檔案訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="223e8-112">Considerations When Creating Flat File Message Schemas</span></span>](../core/considerations-when-creating-flat-file-message-schemas.md)   
-  <span data-ttu-id="223e8-113">**限制的字元 (一般檔案結構描述的節點屬性**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="223e8-113">**Restricted Characters (Node Property of Flat File Schemas** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>