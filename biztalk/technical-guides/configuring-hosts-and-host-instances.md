---
title: 設定主控件和主控件執行個體 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a36a73a4-cc5f-47d6-b56f-7871684c4489
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 286bdaaff66cf0b85caa3bb169bb506501ff386f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968999"
---
# <a name="configuring-hosts-and-host-instances"></a>設定主控件和主控件執行個體
BizTalk 主控件代表零個或多個執行階段程序，在其中您可以部署一組邏輯[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務和成品 （例如配接器處理常式，接收位置，以及協調流程）。 主控件執行個體是實體的執行個體，執行的電腦上主控件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 如需有關 BizTalk 主控件和主控件執行個體的詳細資訊，請參閱 <<c0> [ 主機](http://go.microsoft.com/fwlink/?LinkId=154189)(<http://go.microsoft.com/fwlink/?LinkId=154189>) 及[主控件執行個體](http://go.microsoft.com/fwlink/?LinkId=154190)(<http://go.microsoft.com/fwlink/?LinkId=154190>)。  
  
 如需管理 BizTalk 主控件和主控件執行個體的詳細資訊，請參閱 <<c0> [ 管理 BizTalk 主控件和主控件執行個體](http://go.microsoft.com/fwlink/?LinkId=154191)(http://go.microsoft.com/fwlink/?LinkId=154191)。  
  
 如需有關如何設定專用的追蹤主控件的資訊，請參閱[專用的追蹤主控件設定](../technical-guides/configuring-a-dedicated-tracking-host.md)。  
  
## <a name="separating-host-instances-by-functionality"></a>分隔主控件執行個體的功能  
 除了主控件執行個體組態的高可用性方面，您應該分開傳送、 接收、 處理和追蹤功能到多部主機。 這會設定您的 BizTalk 群組中的工作負載時，提供彈性，而且是將處理分散到 BizTalk 群組的主要方法。 這也可讓您停止一部主機，而不會影響其他主機。 比方說，您可能要停止傳送訊息，讓他們佇列在 MessageBox 資料庫中，同時仍然允許輸入的接收的訊息進行。  
  
 主控件執行個體分隔功能時，也會提供下列優點：  
  
- 每個主控件執行個體有自己的資源，例如記憶體、 控制代碼，以及執行緒集.NET 執行緒集區中。  
  
- 多個 BizTalk 主控件也會減少爭用 MessageBox 資料庫主應用程式佇列資料表，因為每一部主機指派其本身在 MessageBox 資料庫中的工作佇列資料表。  
  
- 節流的實作中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主機層級。 這可讓您設定每個主控件節流特性不同。  
  
- 安全性被實作主機層級;每個主控件是離散的 Windows 身分識別下執行。 這可讓您，比方說，讓**Host_A**存取權**FileShare_B**，同時不允許任何其他主機存取檔案共用。  
  
  > [!NOTE]  
  >  權益，以建立其他主控件執行個體時，也有缺點如果建立太多的主控件執行個體。 每個主控件執行個體是 Windows 服務 （BTSNTSvc.exe 或 BTSNTSvc64.exe），這會產生額外的負載，對 MessageBox 資料庫，並使用電腦資源 （例如 CPU、 記憶體、 執行緒)。  
  
  如需有關修改[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主機內容，請參閱 <<c2> [ 如何修改主機內容](http://go.microsoft.com/fwlink/?LinkId=154192)(<http://go.microsoft.com/fwlink/?LinkId=154192>)。  
  
##  <a name="BKMK_MemLimit"></a> 32 位元 BizTalk 主控件執行個體的記憶體使用量的最大實際的限制  
 32 位元 Windows 作業系統，使用 3 GB 集上的 32 位元處理序有 3 gb 的可定址的記憶體，如果程序 「 注意大型位址 」 （也就是可執行檔有映像標頭中設定的 IMAGE_FILE_LARGE_ADDRESS_AWARE 旗標）。  BizTalk 主控件程序，在 「 大型位址感知 」，可以解決 3 GB 的 3 GB 設定的 Windows 作業系統上的記憶體。  同樣地，在 64 位元 Windows 作業系統 (AMD64) 上的 32 位元處理序都有 4 GB 的可定址的記憶體，如果程序 「 注意大型位址 」。  同樣地，BizTalk 主控件程序中，在 「 大型位址感知 」，可以解決 4 GB 記憶體的 64 位元 Windows 作業系統上執行 32 位元處理序時。 在 64 位元 Windows 作業系統 (AMD64) 上的 64 位元處理序有 8 tb 的可定址的記憶體。  
  
 即使處理程序在 32 位元 Windows 作業系統上 （不含 /3GB 參數） 的可定址的最大記憶體為 2 GB，（例如 BizTalk 主控件執行個體） 的.NET 應用程式之前，會收到記憶體不足的錯誤 「 虛擬位元組 」 達到 2 GB。 下表摘要說明這，並包含虛擬位元組和私用位元組的實際限制。  
  
|處理|Windows 作業系統|可定址的記憶體 （與這個大型位址感知的程序）|虛擬位元組的實際限制|PrivateBytes 的實際限制|  
|-------------|----------------|---------------------------------------------------------------|---------------------------------------|--------------------------------------|  
|32 位元|32 位元|2 GB|1400 MB|800 MB|  
|32 位元|32 位元 3 gb|3 GB|2400 MB|1800 MB|  
|32 位元|64 位元|4 GB|3400 MB|2800 MB|  
|64 位元|64 位元|8 tb|-|-|  
  
 如需詳細資訊，請參閱：  
  
-   [ASP.NET 效能監視和警示系統管理員的時機](http://go.microsoft.com/fwlink/?LinkId=151856)(http://go.microsoft.com/fwlink/?LinkId=151856)  
  
-   [Windows 版本的記憶體限制](http://go.microsoft.com/fwlink/?LinkId=151857)(http://go.microsoft.com/fwlink/?LinkId=151857)  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單： 設定 BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)   
 [設定專用的追蹤主控件](../technical-guides/configuring-a-dedicated-tracking-host.md)