---
title: 在 64 位元 Windows 作業系統上使用 BizTalk Server 時的考量 |Microsoft 文件
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
ms.openlocfilehash: f4c6ac3b8a3104e1c96b2dc9ebd880489d3c9833
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008383"
---
# <a name="considerations-while-using-biztalk-server-on-a-64-bit-windows-operating-system"></a>在 64 位元 Windows 作業系統上使用 BizTalk Server 時的考量
當使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在 64 位元 Windows 作業系統，請確定您考慮本主題中所述的問題。 與 Microsoft BizTalk Server 的 64 位元支援常見問題集的問題，請參閱[BizTalk Server 64 位元支援](http://go.microsoft.com/fwlink/?LinkID=155306)(http://go.microsoft.com/fwlink/?LinkID=155306)。  
  
## <a name="modify-the-process-memory-usage-throttling-threshold"></a>修改 節流處理臨界值的處理序記憶體使用量  
 根據預設，**處理記憶體使用量**主控件節流臨界值設定為 25。 如果超過這個值時，BizTalk 處理序記憶體使用量是 300 MB 以上，可能會發生節流狀況。 在 64 位元伺服器上，您可以增加此值為 100。 這可讓更多的記憶體耗用量 BizTalk 程序之前就會發生節流。 如需有關如何修改程序記憶體使用量主控件節流處理臨界值的指示，請參閱[如何修改預設主控件節流設定](http://go.microsoft.com/fwlink/?LinkId=157210)(http://go.microsoft.com/fwlink/?LinkId=157210)。  
  
> [!NOTE]  
>  就此計算的目的，可用處理序記憶體上限是由 2 GB 的位址空間大小所限制，即使系統擁有 2 GB 以上的實體記憶體依然如此。 此計算的 2 GB 處理序記憶體上限同時適用於 32 位元與 64 位元系統。 為了避免記憶體不足的錯誤，建議您不指定值，將會允許主控件執行個體時執行 32 位元版本的 BizTalk Server 中，不論，如果 BizTalk Server 安裝在 32 位元或 64 位元作業系統 sy 超過 1.54 GB 的記憶體因為。 例如，如果您指定的值從 1 到 100 之間的這項設定來起始處理序使用的記憶體百分比為基礎的節流設定，請勿輸入大於 75 (.75 * 2 GB = 1.54 GB) 的值。 如果您指定的值大於 100，此設定來起始節流根據指定的數字，以 mb 為單位，請勿輸入大於 1536.If 執行 BizTalk Server 的 64 位元版本，指定值或 100 （100%) 或 2048 (2 GB) 起始 節流使用 2 GB 的處理序的最大可用記憶體時。  
  
## <a name="adapters-that-do-not-support-64-bit-hosts"></a>不支援 64 位元主機介面卡。  
 下列配接器不支援在 64 位元主控件執行個體上執行：  
  
-   FTP 配接器  
  
-   POP3 配接器  
  
 請確定您執行這些介面卡的 32 位元主控件執行個體中。  
  
## <a name="configure-the-mimesmime-encoder-to-run-in-32-bit-mode"></a>將 MIME/SMIME 編碼器設定成在 32 位元模式下執行  
 在 BizTalk Server 中，MIME/SMIME 編碼器管線元件還沒有原生 64 位元支援。 這表示，此元件必須在 32 位元模擬模式程序 (WOW64) 中執行。 而這也暗示，在其中執行此編碼器元件的主控件執行個體 (或此元件為其一部分的傳送管線)，必須以 32 位元模擬模式執行。 請注意，這項限制對於在此相同主控件執行個體中執行的其他 BizTalk 項目，也會有效能上 (或其他方面) 的暗示。