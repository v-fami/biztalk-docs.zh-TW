---
title: 在 64 位元 Windows 作業系統上使用 BizTalk Server 時的考量 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac630f55-7ebe-4b93-bf98-70b00788520f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 486df5450c01b51426383e7ab7a3d100013c23dc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990575"
---
# <a name="considerations-while-using-biztalk-server-on-a-64-bit-windows-operating-system"></a><span data-ttu-id="100d6-102">在 64 位元 Windows 作業系統上使用 BizTalk Server 時的考量</span><span class="sxs-lookup"><span data-stu-id="100d6-102">Considerations While Using BizTalk Server on a 64-bit Windows Operating System</span></span>
<span data-ttu-id="100d6-103">當使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]64 位元 Windows 作業系統上，確定您考慮本主題中所述的問題。</span><span class="sxs-lookup"><span data-stu-id="100d6-103">When using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on a 64-bit Windows operating system, make sure you consider the issues described in this topic.</span></span> <span data-ttu-id="100d6-104">Microsoft BizTalk Server 的 64 位元支援的相關常見問題集的問題，請參閱[BizTalk Server 64 位元支援](http://go.microsoft.com/fwlink/?LinkID=155306)(<http://go.microsoft.com/fwlink/?LinkID=155306>)。</span><span class="sxs-lookup"><span data-stu-id="100d6-104">For frequently asked questions related to 64-bit support for Microsoft BizTalk Server, see [BizTalk Server 64-bit Support](http://go.microsoft.com/fwlink/?LinkID=155306) (<http://go.microsoft.com/fwlink/?LinkID=155306>).</span></span>  
  
## <a name="modify-the-process-memory-usage-throttling-threshold"></a><span data-ttu-id="100d6-105">修改節流閾值的程序記憶體使用量</span><span class="sxs-lookup"><span data-stu-id="100d6-105">Modify the Process Memory Usage Throttling Threshold</span></span>  
 <span data-ttu-id="100d6-106">根據預設，**處理序記憶體使用量**主控件節流臨界值設定為 25。</span><span class="sxs-lookup"><span data-stu-id="100d6-106">By default, the **Process memory usage** host throttling threshold is set to 25.</span></span> <span data-ttu-id="100d6-107">如果超過此值時，BizTalk 處理序記憶體使用量是 300 MB 以上，可能會發生節流狀況。</span><span class="sxs-lookup"><span data-stu-id="100d6-107">If this value is exceeded and the BizTalk process memory usage is more than 300 MB, a throttling condition may occur.</span></span> <span data-ttu-id="100d6-108">在 64 位元伺服器上，您可以增加此值為 100。</span><span class="sxs-lookup"><span data-stu-id="100d6-108">On a 64-bit server, you can increase this value to 100.</span></span> <span data-ttu-id="100d6-109">這可讓更多的記憶體耗用量 BizTalk 程序之前就會發生節流。</span><span class="sxs-lookup"><span data-stu-id="100d6-109">This allows for more memory consumption by the BizTalk process before throttling occurs.</span></span> <span data-ttu-id="100d6-110">如需有關如何修改處理程序記憶體使用量主控件節流臨界值的指示，請參閱[如何修改預設主控件節流設定](http://go.microsoft.com/fwlink/?LinkId=157210)(http://go.microsoft.com/fwlink/?LinkId=157210)。</span><span class="sxs-lookup"><span data-stu-id="100d6-110">For instructions on how to modify the process memory usage host throttling threshold, see [How to Modify the Default Host Throttling Settings](http://go.microsoft.com/fwlink/?LinkId=157210) (http://go.microsoft.com/fwlink/?LinkId=157210).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="100d6-111">就此計算的目的，可用處理序記憶體上限是由 2 GB 的位址空間大小所限制，即使系統擁有 2 GB 以上的實體記憶體依然如此。</span><span class="sxs-lookup"><span data-stu-id="100d6-111">The maximum available process memory is capped at an address space size of 2 GB for purposes of this calculation, even if the system has more than 2 GB of physical memory.</span></span> <span data-ttu-id="100d6-112">此計算的 2 GB 處理序記憶體上限同時適用於 32 位元與 64 位元系統。</span><span class="sxs-lookup"><span data-stu-id="100d6-112">A 2 GB process memory upper limit is used for purposes of this calculation on both 32 bit and 64 bit systems.</span></span> <span data-ttu-id="100d6-113">為了避免記憶體不足的錯誤，建議您不指定值，將會允許主控件執行個體記憶體超過 1.54 GB，不論執行 BizTalk Server 的 32 位元版本，如果 BizTalk Server 安裝在 32 位元或 64 位元作業系統 sy 時stem。</span><span class="sxs-lookup"><span data-stu-id="100d6-113">In order to prevent out of memory errors, it is recommended that you do not specify a value that will allow host instance memory to exceed 1.54 GB when running a 32 bit version of BizTalk Server, regardless of if BizTalk Server is installed on a 32 bit or 64 bit operating system.</span></span> <span data-ttu-id="100d6-114">例如，如果您指定 1 到 100，這項設定來開始節流根據使用的處理序記憶體的百分比值時，不輸入大於 75 (字.75 \* 2 GB = 1.54 GB) 的值。</span><span class="sxs-lookup"><span data-stu-id="100d6-114">For example, if you specify a value from 1 through 100 for this setting to initiate throttling based upon the percentage of process memory used, do not enter a value greater than 75 (.75 \* 2GB = 1.54 GB).</span></span> <span data-ttu-id="100d6-115">如果您指定的值大於 100，這項設定來開始節流根據指定的數字，以 mb 為單位，請勿輸入大於 1536.If 執行 BizTalk Server 的 64 位元版本，請指定值或 100 （100%) 或 2048 (2GB) 起始 節流使用 2 gb 的可用處理序的最大記憶體時。</span><span class="sxs-lookup"><span data-stu-id="100d6-115">If you specify a value greater than 100 for this setting to initiate throttling based upon the specified number in MB, do not enter a value greater than 1536.If you are running a 64 bit version of BizTalk Server, specify a value or either 100 (100%) or 2048 (2GB) to initiate throttling when the maximum available process memory of 2 GB is used.</span></span>  
  
## <a name="adapters-that-do-not-support-64-bit-hosts"></a><span data-ttu-id="100d6-116">不支援 64 位元主機介面卡</span><span class="sxs-lookup"><span data-stu-id="100d6-116">Adapters That Do Not Support 64-bit Hosts</span></span>  
 <span data-ttu-id="100d6-117">下列配接器不支援在 64 位元主控件執行個體上執行：</span><span class="sxs-lookup"><span data-stu-id="100d6-117">The following adapters are not supported to run on 64-bit host instances:</span></span>  
  
- <span data-ttu-id="100d6-118">FTP 配接器</span><span class="sxs-lookup"><span data-stu-id="100d6-118">FTP adapter</span></span>  
  
- <span data-ttu-id="100d6-119">POP3 配接器</span><span class="sxs-lookup"><span data-stu-id="100d6-119">POP3 adapter</span></span>  
  
  <span data-ttu-id="100d6-120">請確定您在 32 位元主控件執行個體中執行這些介面卡。</span><span class="sxs-lookup"><span data-stu-id="100d6-120">Make sure you run these adapters in a 32-bit host instance.</span></span>  
  
## <a name="configure-the-mimesmime-encoder-to-run-in-32-bit-mode"></a><span data-ttu-id="100d6-121">設定 MIME/SMIME 編碼器在 32 位元模式下執行</span><span class="sxs-lookup"><span data-stu-id="100d6-121">Configure the MIME/SMIME Encoder to run in 32-bit mode</span></span>  
 <span data-ttu-id="100d6-122">在 BizTalk Server 中，MIME/SMIME 編碼器管線元件就會中斷不會有原生的 64 位元支援。</span><span class="sxs-lookup"><span data-stu-id="100d6-122">In BizTalk Server, the MIME/SMIME encoder pipeline component dies not have native 64-bit support.</span></span> <span data-ttu-id="100d6-123">這表示，此元件必須在 32 位元模擬模式程序 (WOW64) 中執行。</span><span class="sxs-lookup"><span data-stu-id="100d6-123">This means that this component must be run in a 32-bit emulation mode process (WOW64).</span></span> <span data-ttu-id="100d6-124">而這也暗示，在其中執行此編碼器元件的主控件執行個體 (或此元件為其一部分的傳送管線)，必須以 32 位元模擬模式執行。</span><span class="sxs-lookup"><span data-stu-id="100d6-124">This implies that the host instance in which this encoder component (or the send pipeline of which it is a part) runs must be running in 32-bit emulation mode.</span></span> <span data-ttu-id="100d6-125">請注意，這項限制對於在此相同主控件執行個體中執行的其他 BizTalk 項目，也會有效能上 (或其他方面) 的暗示。</span><span class="sxs-lookup"><span data-stu-id="100d6-125">Be aware of the performance (and other) implications of this restriction for other elements of BizTalk running in this same host instance.</span></span>