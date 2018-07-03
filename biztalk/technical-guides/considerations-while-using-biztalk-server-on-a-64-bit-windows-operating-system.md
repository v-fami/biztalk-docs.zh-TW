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
# <a name="considerations-while-using-biztalk-server-on-a-64-bit-windows-operating-system"></a>在 64 位元 Windows 作業系統上使用 BizTalk Server 時的考量
當使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]64 位元 Windows 作業系統上，確定您考慮本主題中所述的問題。 Microsoft BizTalk Server 的 64 位元支援的相關常見問題集的問題，請參閱[BizTalk Server 64 位元支援](http://go.microsoft.com/fwlink/?LinkID=155306)(<http://go.microsoft.com/fwlink/?LinkID=155306>)。  
  
## <a name="modify-the-process-memory-usage-throttling-threshold"></a>修改節流閾值的程序記憶體使用量  
 根據預設，**處理序記憶體使用量**主控件節流臨界值設定為 25。 如果超過此值時，BizTalk 處理序記憶體使用量是 300 MB 以上，可能會發生節流狀況。 在 64 位元伺服器上，您可以增加此值為 100。 這可讓更多的記憶體耗用量 BizTalk 程序之前就會發生節流。 如需有關如何修改處理程序記憶體使用量主控件節流臨界值的指示，請參閱[如何修改預設主控件節流設定](http://go.microsoft.com/fwlink/?LinkId=157210)(http://go.microsoft.com/fwlink/?LinkId=157210)。  
  
> [!NOTE]  
>  就此計算的目的，可用處理序記憶體上限是由 2 GB 的位址空間大小所限制，即使系統擁有 2 GB 以上的實體記憶體依然如此。 此計算的 2 GB 處理序記憶體上限同時適用於 32 位元與 64 位元系統。 為了避免記憶體不足的錯誤，建議您不指定值，將會允許主控件執行個體記憶體超過 1.54 GB，不論執行 BizTalk Server 的 32 位元版本，如果 BizTalk Server 安裝在 32 位元或 64 位元作業系統 sy 時stem。 例如，如果您指定 1 到 100，這項設定來開始節流根據使用的處理序記憶體的百分比值時，不輸入大於 75 (字.75 * 2 GB = 1.54 GB) 的值。 如果您指定的值大於 100，這項設定來開始節流根據指定的數字，以 mb 為單位，請勿輸入大於 1536.If 執行 BizTalk Server 的 64 位元版本，請指定值或 100 （100%) 或 2048 (2GB) 起始 節流使用 2 gb 的可用處理序的最大記憶體時。  
  
## <a name="adapters-that-do-not-support-64-bit-hosts"></a>不支援 64 位元主機介面卡  
 下列配接器不支援在 64 位元主控件執行個體上執行：  
  
- FTP 配接器  
  
- POP3 配接器  
  
  請確定您在 32 位元主控件執行個體中執行這些介面卡。  
  
## <a name="configure-the-mimesmime-encoder-to-run-in-32-bit-mode"></a>設定 MIME/SMIME 編碼器在 32 位元模式下執行  
 在 BizTalk Server 中，MIME/SMIME 編碼器管線元件就會中斷不會有原生的 64 位元支援。 這表示，此元件必須在 32 位元模擬模式程序 (WOW64) 中執行。 而這也暗示，在其中執行此編碼器元件的主控件執行個體 (或此元件為其一部分的傳送管線)，必須以 32 位元模擬模式執行。 請注意，這項限制對於在此相同主控件執行個體中執行的其他 BizTalk 項目，也會有效能上 (或其他方面) 的暗示。