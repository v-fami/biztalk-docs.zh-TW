---
title: POP3 配接器的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b6d621a2-4801-44fe-a266-d4c05ac82633
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bc86b2ae14b04b160f7387f870615116e659b3f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22261942"
---
# <a name="known-issues-with-the-pop3-adapter"></a><span data-ttu-id="82d47-102">POP3 配接器的已知問題</span><span class="sxs-lookup"><span data-stu-id="82d47-102">Known Issues with the POP3 Adapter</span></span>
<span data-ttu-id="82d47-103">本節包含可幫助您避免錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="82d47-103">This section contains information that may help you avoid errors.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="82d47-104">已知問題</span><span class="sxs-lookup"><span data-stu-id="82d47-104">Known Issues</span></span>  
  
#### <a name="the-pop3-adapter-fails-to-process-documents-when-running-on-a-64-bit-operating-system"></a><span data-ttu-id="82d47-105">POP3 配接器在 64 位元作業系統上執行時，無法處理文件</span><span class="sxs-lookup"><span data-stu-id="82d47-105">The POP3 Adapter fails to process documents when running on a 64 bit operating system</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="82d47-106">問題</span><span class="sxs-lookup"><span data-stu-id="82d47-106">Problem</span></span>  
 <span data-ttu-id="82d47-107">POP3 配接器在 64 位元作業系統上執行時，將無法處理文件。</span><span class="sxs-lookup"><span data-stu-id="82d47-107">The POP3 Adapter will not process documents when running on a 64 bit operating system.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="82d47-108">原因</span><span class="sxs-lookup"><span data-stu-id="82d47-108">Cause</span></span>  
 <span data-ttu-id="82d47-109">POP3 配接器處理常式無法在 64 位元主控件執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="82d47-109">The POP3 Adapter adapter handler is unable to run in a 64 bit host instance.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="82d47-110">解決方案</span><span class="sxs-lookup"><span data-stu-id="82d47-110">Resolution</span></span>  
 <span data-ttu-id="82d47-111">如果您在 64 位元電腦上執行 POP3 配接器，則必須設定 POP3 配接器處理常式，使其在 32 位元主控件中執行。</span><span class="sxs-lookup"><span data-stu-id="82d47-111">If you are running the POP3 Adapter on a 64 bit machine, configure the POP3 Adapter handlers to run in a 32 bit host.</span></span> <span data-ttu-id="82d47-112">此選項可在 [主控件屬性] 頁面上取得，您可從 BizTalk 管理主控台存取此頁面。</span><span class="sxs-lookup"><span data-stu-id="82d47-112">This option is available on the Host Properties page accessible from the BizTalk Administration console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82d47-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82d47-113">See Also</span></span>  
 [<span data-ttu-id="82d47-114">POP3 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="82d47-114">Troubleshooting the POP3 Adapter</span></span>](../core/troubleshooting-the-pop3-adapter.md)