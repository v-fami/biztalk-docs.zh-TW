---
title: 設定主控件和主控件執行個體 |Microsoft 文件
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
ms.openlocfilehash: 55dda06d447d9e27c7c8b491986b499003c0bb73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22300110"
---
# <a name="configuring-hosts-and-host-instances"></a>設定主控件和主控件執行個體
BizTalk 主控件代表零個或多個執行階段處理序中，您可以部署一組邏輯[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務和成品 （例如配接器處理常式，接收位置，以及協調流程）。 主控件執行個體是執行的電腦上的主機的實體執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 如需 BizTalk 主控件和主控件執行個體的詳細資訊，請參閱[主機](http://go.microsoft.com/fwlink/?LinkId=154189)(http://go.microsoft.com/fwlink/?LinkId=154189) 和[主控件執行個體](http://go.microsoft.com/fwlink/?LinkId=154190)(http://go.microsoft.com/fwlink/?LinkId=154190)。  
  
 如需管理 BizTalk 主控件和主控件執行個體的詳細資訊，請參閱[管理 BizTalk 主控件和主控件執行個體](http://go.microsoft.com/fwlink/?LinkId=154191)(http://go.microsoft.com/fwlink/?LinkId=154191)。  
  
 如需如何設定專用的追蹤主控件的資訊，請參閱[專用的追蹤主控件設定](../technical-guides/configuring-a-dedicated-tracking-host.md)。  
  
## <a name="separating-host-instances-by-functionality"></a>分隔主控件執行個體的功能  
 除了主控件執行個體組態的高可用性方面，您應該個別傳送、 接收、 處理及追蹤功能分成多個主控件。 這提供彈性，設定 BizTalk 群組中的工作負載時，將處理分散到 BizTalk 群組的主要方法。 這也可讓您停止一部主機，而不會影響其他主機。 比方說，您可能想要停止傳送訊息，通知他們佇列在 MessageBox 資料庫中，同時，仍允許輸入的接收的訊息。  
  
 分隔主控件執行個體功能也會提供下列優點：  
  
-   每個主控件執行個體的.NET 執行緒集區中有它自己的資源，例如記憶體、 控制代碼，以及執行緒集。  
  
-   多個 BizTalk 主控件也會減少 MessageBox 資料庫主應用程式佇列資料表上的競爭，因為每一部主機指派自己 MessageBox 資料庫中的工作佇列資料表。  
  
-   節流中實作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主機層級。 這可讓您設定每個主控件節流的特性不同。  
  
-   在主機層級; 實作安全性每一部主機會使用不連續的 Windows 身分識別下執行。 這樣可讓您，例如，若要讓**Host_A**存取**FileShare_B**，同時不允許任何其他主機，才能存取檔案共用。  
  
    > [!NOTE]  
    >  優點，可建立其他主控件執行個體時，也有缺點如果太多的主控件執行個體所建立。 每個主控件執行個體是 Windows 服務 （BTSNTSvc.exe 或 BTSNTSvc64.exe） 會產生對 MessageBox 資料庫的額外負載，並使用電腦資源 （例如 CPU、 記憶體、 執行緒)。  
  
 如需有關修改[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主機內容，請參閱[如何修改主機內容](http://go.microsoft.com/fwlink/?LinkId=154192)(http://go.microsoft.com/fwlink/?LinkId=154192)。  
  
##  <a name="BKMK_MemLimit"></a>32 位元 BizTalk 主控件執行個體的記憶體使用量的最大實際限制  
 在 32 位元 Windows 作業系統，使用 3 GB 組上的 32 位元處理序有 3 gb 的可定址的記憶體的程序是 「 大位址感知 」 （也就是可執行檔有映像標頭中設定的 IMAGE_FILE_LARGE_ADDRESS_AWARE 旗標）。  BizTalk 主控件程序的 「 大型位址注意 」，可以解決 3 GB 的記憶體使用 3 GB 組的 Windows 作業系統上。  同樣地，如果程序是 「 大位址注意 」 在 64 位元 Windows 作業系統 (AMD64) 上的 32 位元處理序有 4 GB 的可定址的記憶體。  同樣地，BizTalk 主控件程序，在 「 大位址注意 」，可以解決 4 GB 的記憶體 64 位元 Windows 作業系統上以 32 位元處理序方式執行。 在 64 位元 Windows 作業系統 (AMD64) 上的 64 位元處理序有 8 tb 的可定址的記憶體。  
  
 即使可定址在 32 位元 Windows 作業系統上 （不含 /3GB 參數） 處理程序的記憶體上限是 2 GB，.NET 應用程式 （例如 BizTalk 主控件執行個體） 之前，會收到記憶體不足錯誤的 「 虛擬位元組 」 達到 2 GB。 下表摘要說明此，並包含虛擬位元組和私用位元組的實際限制。  
  
|處理|Windows 作業系統|可定址的記憶體 （以大型位址感知處理程序）|虛擬位元組的實際限制|PrivateBytes 的實際限制|  
|-------------|----------------|---------------------------------------------------------------|---------------------------------------|--------------------------------------|  
|32 位元|32 位元|2 GB|1400 MB|800 MB|  
|32 位元|32 位元 3 gb|3 GB|2400 MB|1800 MB|  
|32 位元|64 位元|4 GB|3400 MB|2800 MB|  
|64 位元|64 位元|為 8 tb|-|-|  
  
 如需詳細資訊，請參閱：  
  
-   [ASP.NET 效能監視和警示系統管理員的時機](http://go.microsoft.com/fwlink/?LinkId=151856)(http://go.microsoft.com/fwlink/?LinkId=151856)  
  
-   [Windows 版本的記憶體限制](http://go.microsoft.com/fwlink/?LinkId=151857)(http://go.microsoft.com/fwlink/?LinkId=151857)  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單： 設定 BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)   
 [專用的追蹤主控件設定](../technical-guides/configuring-a-dedicated-tracking-host.md)