---
title: 如何指派訊息內容屬性 Values1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7e76c62-3110-482c-8083-84d411e6f475
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 39bb2a4c6520c1ff3a21889e7508bb2cf417b817
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247302"
---
# <a name="how-to-assign-message-context-property-values"></a><span data-ttu-id="496bc-102">如何指派訊息內容屬性值</span><span class="sxs-lookup"><span data-stu-id="496bc-102">How to Assign Message Context Property Values</span></span>
<span data-ttu-id="496bc-103">若要從 BizTalk 協調流程管理 JD Edwards EnterpriseOne 配接器連接工作階段，則必須在專案中加入對 Microsoft.BizTalk.Adapters.JDEProperties.dll 的參照。</span><span class="sxs-lookup"><span data-stu-id="496bc-103">To manage the JD Edwards EnterpriseOne Adapter connection session from a BizTalk orchestration, you must add the reference to Microsoft.BizTalk.Adapters.JDEProperties.dll in your project.</span></span> <span data-ttu-id="496bc-104">這個組件位於 %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin。</span><span class="sxs-lookup"><span data-stu-id="496bc-104">This assembly is located in %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin.</span></span>  
  
 <span data-ttu-id="496bc-105">在參考這個屬性結構描述之後，即可讓各種 BizTalk 開發工具存取其他的內容屬性。例如，在「協調流程設計師」內的「訊息指派」圖形。</span><span class="sxs-lookup"><span data-stu-id="496bc-105">After you reference this property schema, additional context properties are accessible to various BizTalk development tools, for example, the Message Assignment shape within the Orchestration Designer.</span></span>  
  
 <span data-ttu-id="496bc-106">若要存取內容屬性，則必須在 JD Edwards EnterpriseOne 命名空間內指定其中一個可用的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="496bc-106">To access a context property, you specify one of the available context properties within the JD Edwards EnterpriseOne namespace.</span></span> <span data-ttu-id="496bc-107">若要讀取已繫結至 Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 之連接埠所接收訊息的內容屬性，請在運算式中使用 Message(JDE.Property) 的語法。</span><span class="sxs-lookup"><span data-stu-id="496bc-107">To read a context property of a message received from a port bound to the Microsoft BizTalk Adapter for JD Edwards EnterpriseOne, use the syntax, Message(JDE.Property), in an expression.</span></span> <span data-ttu-id="496bc-108">如需屬性清單，請參閱「JD Edwards EnterpriseOne 配接器工作階段管理」。</span><span class="sxs-lookup"><span data-stu-id="496bc-108">Refer to JD Edwards EnterpriseOne Adapter Session Management for a list of properties.</span></span>  
  
 <span data-ttu-id="496bc-109">在 BizTalk 中，訊息都是不變的。</span><span class="sxs-lookup"><span data-stu-id="496bc-109">In BizTalk, messages are immutable.</span></span>  
  
### <a name="to-assign-context-property-value"></a><span data-ttu-id="496bc-110">若要指派內容屬性值</span><span class="sxs-lookup"><span data-stu-id="496bc-110">To assign context property value</span></span>  
  
1.  <span data-ttu-id="496bc-111">建立新的訊息。</span><span class="sxs-lookup"><span data-stu-id="496bc-111">Create a new message.</span></span>  
  
2.  <span data-ttu-id="496bc-112">設定訊息內容，例如，藉由指派現有的訊息。</span><span class="sxs-lookup"><span data-stu-id="496bc-112">Set the message content, for example, by assigning an existing message.</span></span>  
  
3.  <span data-ttu-id="496bc-113">設定屬性。</span><span class="sxs-lookup"><span data-stu-id="496bc-113">Set the properties.</span></span>  
  
 <span data-ttu-id="496bc-114">若要為目的地為已繫結至 Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 之傳送埠的訊息指派內容屬性，請使用訊息指派運算子。</span><span class="sxs-lookup"><span data-stu-id="496bc-114">To assign context properties to a message destined to a send port that is bound to the Microsoft BizTalk Adapter for JD Edwards EnterpriseOne, use the message assignment operator.</span></span> <span data-ttu-id="496bc-115">然後在 JD Edwards EnterpriseOne 命名空間內指定其中一個可用的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="496bc-115">Then specify one of the available context properties within the JD Edwards EnterpriseOne namespace.</span></span>  
  
 <span data-ttu-id="496bc-116">語法如下：`Message(JDE.Property) = value;`</span><span class="sxs-lookup"><span data-stu-id="496bc-116">The syntax is: `Message(JDE.Property) = value;`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="496bc-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="496bc-117">See Also</span></span>  
 <span data-ttu-id="496bc-118">[使用訊息內容屬性](../core/using-message-context-properties1.md) </span><span class="sxs-lookup"><span data-stu-id="496bc-118">[Using Message Context Properties](../core/using-message-context-properties1.md) </span></span>  
 <span data-ttu-id="496bc-119">[關於工作階段管理](../core/about-session-management2.md) </span><span class="sxs-lookup"><span data-stu-id="496bc-119">[About Session Management](../core/about-session-management2.md) </span></span>  
 [<span data-ttu-id="496bc-120">教學課程： 使用 BizTalk Adapter for JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="496bc-120">Tutorial: Using the BizTalk Adapter for JD Edwards EnterpriseOne</span></span>](../core/tutorial-using-the-biztalk-adapter-for-jd-edwards-enterpriseone.md)