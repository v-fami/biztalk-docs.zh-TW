---
title: 傳送保留批次與 XML 傳送管線 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6765576a-134f-4856-911c-2f603b6479bd
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 14bd61538398bb11967cbbe750a4fadc016a5168
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269822"
---
# <a name="sending-a-preserved-batch-with-an-xml-send-pipeline"></a><span data-ttu-id="aca09-102">透過 XML 傳送管線來傳送保留批次</span><span class="sxs-lookup"><span data-stu-id="aca09-102">Sending a Preserved Batch with an XML Send Pipeline</span></span>
<span data-ttu-id="aca09-103">通常保留批次會透過 EDI 傳送管線來傳送。</span><span class="sxs-lookup"><span data-stu-id="aca09-103">Normally, a preserved batch is sent using an EDI send pipeline.</span></span> <span data-ttu-id="aca09-104">但是，您也可以使用 XML 傳送管線來傳送保留批次。</span><span class="sxs-lookup"><span data-stu-id="aca09-104">However, you can also use an XML send pipeline to send a preserved batch.</span></span> <span data-ttu-id="aca09-105">因為 EDI 接收管線所產生和放入 MessageBox 中的保留批次具有 XML 格式，所以 XML 傳送管線可以逐一處理 XML 格式的批次。</span><span class="sxs-lookup"><span data-stu-id="aca09-105">Since the preserved batch that is generated and dropped in the MessageBox by the EDI receive pipeline is in the XML format, the XML send pipeline would pass along the batch in XML format.</span></span>  
  
 <span data-ttu-id="aca09-106">若要透過 XML 傳送管線來傳送保留批次，您必須針對交換中的每種訊息類型，部署具有適用之批次結構描述和文件結構描述的專案。</span><span class="sxs-lookup"><span data-stu-id="aca09-106">To send a preserved batch using the XML send pipeline, you have to deploy a project with the applicable batch schema and the document schemas for each message type in the interchange.</span></span> <span data-ttu-id="aca09-107">此外，您也需要針對您在專案中所部署的批次結構描述變更其命名空間。</span><span class="sxs-lookup"><span data-stu-id="aca09-107">In addition, you also have to change the namespace for the batch schema that you deploy in the project.</span></span> <span data-ttu-id="aca09-108">若沒有這樣做，在保留批次 XML 檔案中的命名空間就無法對應到該批次結構描述的命名空間。</span><span class="sxs-lookup"><span data-stu-id="aca09-108">If you do not do so, the namespace in the preserved batch XML file would not correspond to the namespace for the batch schema.</span></span> <span data-ttu-id="aca09-109">您必須依據下表方式來變更該批次結構描述的命名空間：</span><span class="sxs-lookup"><span data-stu-id="aca09-109">You have to change the namespace for the batch schema as shown in the following table:</span></span>  
  
|<span data-ttu-id="aca09-110">對於這種編碼類型：</span><span class="sxs-lookup"><span data-stu-id="aca09-110">For this encoding type:</span></span>|<span data-ttu-id="aca09-111">變更在批次結構描述中的這個命名空間：</span><span class="sxs-lookup"><span data-stu-id="aca09-111">Change this namespace in the batch schema:</span></span>|<span data-ttu-id="aca09-112">對於下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="aca09-112">To the following namespace:</span></span>|  
|-----------------------------|------------------------------------------------|---------------------------------|  
|<span data-ttu-id="aca09-113">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="aca09-113">EDIFACT</span></span>|`http://schemas.microsoft.com/Edi/Edifact`|`http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006/InterchangeXML`|  
|<span data-ttu-id="aca09-114">X12</span><span class="sxs-lookup"><span data-stu-id="aca09-114">X12</span></span>|`http://schemas.microsoft.com/Edi/X12_BatchSchema`|`http://schemas.microsoft.com/BizTalk/EDI/X12/2006/InterchangeXML`|  
  
 <span data-ttu-id="aca09-115">這些變更作業與 EDI 組合器無關。</span><span class="sxs-lookup"><span data-stu-id="aca09-115">This is not an issue with the EDI Assembler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca09-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aca09-116">See Also</span></span>  
 [<span data-ttu-id="aca09-117">設定 EDI 批次</span><span class="sxs-lookup"><span data-stu-id="aca09-117">Configuring EDI Batches</span></span>](../core/configuring-edi-batches.md)