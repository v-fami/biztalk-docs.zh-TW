---
title: 測試結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2e28b7c-9d0c-4336-8bee-4599d41a57f4
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc036be84bb64e794e6109e1ebc4ec730f382878
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023108"
---
# <a name="testing-schemas"></a><span data-ttu-id="9789f-102">測試結構描述</span><span class="sxs-lookup"><span data-stu-id="9789f-102">Testing Schemas</span></span>
<span data-ttu-id="9789f-103">建立結構描述之後，您可能會想要驗證它是否描述您想要它描述的 XML 結構。</span><span class="sxs-lookup"><span data-stu-id="9789f-103">After you have created your schema, you may want to validate that it describes the XML structure you intend it to describe.</span></span> <span data-ttu-id="9789f-104">您可在您的結構描述上執行下列三種作業來進行驗證：</span><span class="sxs-lookup"><span data-stu-id="9789f-104">You can perform the following three operations on your schema to validate it:</span></span>  
  
- <span data-ttu-id="9789f-105">**執行個體產生**。</span><span class="sxs-lookup"><span data-stu-id="9789f-105">**Instance generation**.</span></span> <span data-ttu-id="9789f-106">此作業會從結構描述產生執行個體訊息、建立要伴隨結構描述所指定之 XML 項目和屬性的測試資料。</span><span class="sxs-lookup"><span data-stu-id="9789f-106">This operation generates an instance message from a schema, creating test data to accompany the XML elements and attributes specified by the schema.</span></span>  
  
- <span data-ttu-id="9789f-107">**結構描述驗證**。</span><span class="sxs-lookup"><span data-stu-id="9789f-107">**Schema validation**.</span></span> <span data-ttu-id="9789f-108">此作業會驗證結構描述的內部一致性，確保它符合「XML 結構描述定義」(XSD) 語言結構描述標準。</span><span class="sxs-lookup"><span data-stu-id="9789f-108">This operation validates the internal consistency of a schema, assuring that it conforms to the XML Schema definition (XSD) language schema standard.</span></span>  
  
- <span data-ttu-id="9789f-109">**執行個體驗證**。</span><span class="sxs-lookup"><span data-stu-id="9789f-109">**Instance validation**.</span></span> <span data-ttu-id="9789f-110">此作業會依據結構描述，驗證指定的執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="9789f-110">This operation validates a given instance message against a schema.</span></span>  
  
  <span data-ttu-id="9789f-111">在將您的結構描述應用於生產環境之前，使用這三種作業先進行測試會很有用。</span><span class="sxs-lookup"><span data-stu-id="9789f-111">All three of these operations are useful for testing your schemas before putting them into use in a production environment.</span></span>  
  
  <span data-ttu-id="9789f-112">本節將詳細描述這些作業。</span><span class="sxs-lookup"><span data-stu-id="9789f-112">This section describes these operations in greater detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9789f-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="9789f-113">In This Section</span></span>  
  
-   [<span data-ttu-id="9789f-114">如何驗證在 Visual Studio 中的結構描述</span><span class="sxs-lookup"><span data-stu-id="9789f-114">How to Validate Schemas in Visual Studio</span></span>](../core/how-to-validate-schemas-in-visual-studio.md)  
  
-   [<span data-ttu-id="9789f-115">如何驗證執行個體訊息</span><span class="sxs-lookup"><span data-stu-id="9789f-115">How to Validate Instance Messages</span></span>](../core/how-to-validate-instance-messages.md)  
  
-   [<span data-ttu-id="9789f-116">如何產生執行個體訊息</span><span class="sxs-lookup"><span data-stu-id="9789f-116">How to Generate Instance Messages</span></span>](../core/how-to-generate-instance-messages.md)