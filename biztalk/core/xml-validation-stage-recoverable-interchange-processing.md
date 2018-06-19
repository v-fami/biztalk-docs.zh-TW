---
title: XML 驗證階段 （可復原交換處理） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1ed00971-d85b-4adb-86c4-c56de7ba7c67
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de8f0225e100053fe6dced8165b7fc800c5e4804
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289950"
---
# <a name="xml-validation-stage-recoverable-interchange-processing"></a><span data-ttu-id="afb4e-102">XML 驗證階段 (可復原交換處理)</span><span class="sxs-lookup"><span data-stu-id="afb4e-102">XML Validation Stage (Recoverable Interchange Processing)</span></span>
<span data-ttu-id="afb4e-103">**XML 驗證器**管線元件會處理交換，在兩種模式：</span><span class="sxs-lookup"><span data-stu-id="afb4e-103">The **XML validator** pipeline component processes an interchange in two modes:</span></span>  
  
-   <span data-ttu-id="afb4e-104">**標準模式**。</span><span class="sxs-lookup"><span data-stu-id="afb4e-104">**Standard mode**.</span></span> <span data-ttu-id="afb4e-105">當**XML 驗證器**元件設定為執行標準驗證、 交易式工作單位來驗證交換中包含的訊息。</span><span class="sxs-lookup"><span data-stu-id="afb4e-105">When the **XML validator** component is configured to perform standard validation, the messages contained in an interchange are validated in a transactional unit of work.</span></span> <span data-ttu-id="afb4e-106">特別是如果驗證交換中的訊息失敗，就會將整個交換 (包含所有訊息) 放入擱置佇列。</span><span class="sxs-lookup"><span data-stu-id="afb4e-106">Specifically, if validation of a message in the interchange fails, the entire interchange (containing all the messages) is placed in the suspended queue.</span></span>  
  
-   <span data-ttu-id="afb4e-107">**可復原模式**。</span><span class="sxs-lookup"><span data-stu-id="afb4e-107">**Recoverable mode**.</span></span> <span data-ttu-id="afb4e-108">當**XML 驗證器**元件設定執行可復原交換處理時，如果訊息的驗證失敗，訊息放入擱置佇列和**XML 驗證器**元件會繼續驗證交換中的其餘訊息。</span><span class="sxs-lookup"><span data-stu-id="afb4e-108">When the **XML validator** component is configured to perform recoverable interchange processing, if validation of a message fails, the message is placed in the suspended queue and the **XML validator** component continues to validate remaining messages in the interchange.</span></span>  
  
### <a name="to-configure-recoverable-interchange-processing"></a><span data-ttu-id="afb4e-109">設定可復原交換處理</span><span class="sxs-lookup"><span data-stu-id="afb4e-109">To configure recoverable interchange processing</span></span>  
  
1.  <span data-ttu-id="afb4e-110">在 Visual Studio 中使用管線設計師來開啟接收管線。</span><span class="sxs-lookup"><span data-stu-id="afb4e-110">Open a receive pipeline by using pipeline designer in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="afb4e-111">拖曳**XML 驗證器**元件從**工具箱**至**驗證**接收管線階段。</span><span class="sxs-lookup"><span data-stu-id="afb4e-111">Drag **XML validator** component from the **Toolbox** to the **Validate** stage of the receive pipeline.</span></span>  
  
3.  <span data-ttu-id="afb4e-112">在 [屬性] 視窗中設定的值**可復原交換處理**屬性**True**如果您想**XML 驗證器**元件至處理程序交換在可復原模式中，或將屬性設定為**False**如果您想要處理交換在標準模式的元件。</span><span class="sxs-lookup"><span data-stu-id="afb4e-112">In the Properties window, set the value of the **Recoverable Interchange Processing** property to **True** if you want the **XML validator** component to process interchanges in the recoverable mode, or set the property to **False** if you want the component to process interchanges in the standard mode.</span></span> <span data-ttu-id="afb4e-113">這個屬性的預設值是`False`。</span><span class="sxs-lookup"><span data-stu-id="afb4e-113">The default value of this property is `False`.</span></span>  
  
 <span data-ttu-id="afb4e-114">**XMLValidator**類別中物件模型中，對應至**XML 驗證器**管線元件，有一個名為的公用屬性**RecoverableInterchangeProcessing**可用來以程式設計方式取得或設定模式。</span><span class="sxs-lookup"><span data-stu-id="afb4e-114">The **XMLValidator** class in the object model, which corresponds to the **XML validator** pipeline component, has a public property named **RecoverableInterchangeProcessing** that you can use to get/set the mode programmatically.</span></span> <span data-ttu-id="afb4e-115">請參閱文件[Microsoft.BizTalk.Component.XmlValidator](http://msdn.microsoft.com/library/microsoft.biztalk.component.xmlvalidator.aspx)類別，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="afb4e-115">See documentation for [Microsoft.BizTalk.Component.XmlValidator](http://msdn.microsoft.com/library/microsoft.biztalk.component.xmlvalidator.aspx) class for more information.</span></span>  
  
 <span data-ttu-id="afb4e-116">已順利驗證的訊息會根據父交換抵達的接收連接埠所設定的合作對象，來識別其傳送合作對象。</span><span class="sxs-lookup"><span data-stu-id="afb4e-116">Messages that are successfully validated have their sending party identified according to the party configured for the receive port on which the parent interchange arrived.</span></span> <span data-ttu-id="afb4e-117">對於任何從交換擷取的訊息，若合作對象解析失敗，則整個交換的合作對象解析就會被視為已失敗。</span><span class="sxs-lookup"><span data-stu-id="afb4e-117">If party resolution for any message extracted from the interchange fails, then the party resolution is considered to have failed for the entire interchange.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb4e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afb4e-118">See Also</span></span>  
 [<span data-ttu-id="afb4e-119">如何設定 XML 驗證器管線元件</span><span class="sxs-lookup"><span data-stu-id="afb4e-119">How to Configure the XML Validator Pipeline Component</span></span>](../core/how-to-configure-the-xml-validator-pipeline-component.md)