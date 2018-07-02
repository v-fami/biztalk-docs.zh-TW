---
title: 向外擴充接收主控件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9f78710-93fa-4877-8273-a1634d768d88
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 650042a5de59410f932af260ee6ca2cfc0a56d77
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985703"
---
# <a name="scaling-out-receiving-hosts"></a>向外擴充接收主控件
若要讓接收主控件高度可用，您必須有兩個或多個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行每個接收主控件執行個體的電腦。 藉由向外擴充接收主控件中，您可以增加 BizTalk Server 部署的是需要大量傳訊的可用性。 雖然這些部署有可能執行最少的協調流程處理，不過它們仍可以最快的速度並提供最大的可靠性來路由許多不同類型的訊息。  
  
 您可以將接收主控件與處理協調流程和傳送訊息的主控件分開，藉此個別保護和擴充其他主控件的每個主控件，提升環境的安全性與擴充性。 例如，您可以將兩部電腦 (主控件執行個體) 新增至接收主控件，而不需將任何電腦新增至處理或傳送主控件。  
  
## <a name="understanding-in-process-and-isolated-receiving-hosts"></a>了解內含式與外掛式接收主控件  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 整合來提供商務服務的應用程式。 整合通常表示為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]收到文件 （從應用程式）、 處理文件，並將傳送處理的文件傳回給應用程式或其他應用程式。 此程序會呼叫文件交易。  
  
 交易通常會開始監視特定的通訊協定通道和接收文件的 BizTalk 介面卡。 *配接器*由於它會連接到其他應用程式，因此呼叫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 根據其函式，它可以是傳送配接器或接收配接器。 預設介面卡的大部分都是使用接收函式和內建在一個.NET 組件的傳送函式的一個.NET 元件。 根據配接器所在的處理序記憶體空間，很可能是同處理序 （接收） 配接器 」 或 「 外掛式 （接收） 配接器。 內含式配接器只可由裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]程序 (BTSNTSvc.exe) 和外掛式配接器設計來裝載另一個處理序。 例如，HTTP 配接器和 SOAP 配接器裝載 Internet Information Services (IIS) 處理序。 也就是基本上 ISAPI 擴充程式。 相反地，所有傳送配接器都是內含式配接器。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定會建立兩個預設的主控件，內含式主控件稱為 [biztalkserverapplication]，而外掛式主控件則稱為 BizTalkServerIsolatedHost。 主機具有兩種功能： 一個以邏輯方式分組[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]項目，因此這些項目可以指派不同[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理程序和其他控制安全性。 您必須指定主機的 Windows 群組。 只有此群組中的使用者可以將文件傳送到所裝載的介面卡*主控件執行個體*指派給此主機。  
  
 兩個預設的主控件的每個有主控件執行個體。 主控件執行個體並沒有名稱，但與主機相關聯。 BizTalkServerApplication 主控件執行個體是實際上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務上的處理程序 (BTSNTSvc.exe) [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BizTalk 群組中的電腦。 BizTalkServerIsolatedHost 主控件執行個體是未直接繫結至處理程序。 它是與裝載接收配接器的處理序相關聯。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定也會建立*接收處理常式*SMTP 除了預設的配接器的每個 （SMTP 是傳送配接器）。 接收處理常式屬性的其中一個是主機名稱。 這就是如何它繫結至主控件與該主控件的主控件執行個體。  
  
 除了配接器、 主機、 主控件執行個體，而且接收處理常式，您必須設定接收埠之前[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以開始接收文件。 接收埠包含接收位置。 接收位置都具有接收處理常式屬性。 邏輯，您可以追蹤[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理這樣的處理程序接收埠。  
  
 在接收連接埠組態中，您可以選擇性地指定對應。 在接收位置組態中，您必須指定用來前置處理文件的管線。 指定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理序會處理接收的文件，來前置處理文件中的，對應文件的所有項目。 這是內含式主控件執行個體和外掛式主控件執行個體相同。  
  
## <a name="scaling-out-in-process-receiving-hosts"></a>相應放大內含式接收裝載  
 下圖顯示 BizTalk Server 部署，另一部電腦上有兩個主控件執行個體每個接收主控件提供高可用性。 請注意，在此圖中的處理和傳送主控件不是高可用性，因為只有一個主控件執行個體處理 BizTalk 項目指派給主機。  
  
 ![多個主控件接收訊息](../core/media/tdi-ha-scalereceive.gif "TDI_HA_ScaleReceive")  
  
 在大型部署、處理多個交易夥伴的實例，以及使用不同通訊協定的實例方面，您可以在多個接收主控件之間分佈接收功能。 例如，您可以為每個配接器建立接收訊息的主控件，或是建立不同的主控件以接收不同夥伴的訊息。 當您建立多個接收主控件時，您可以建立安全範圍並讓環境更容易管理和擴充，不過，它並不會使環境變得高度可用。 為了使環境變得高度可用，您必須為每個建立的接收主控件建立兩個或以上的主控件執行個體。 例如，您可以建立三個不同接收主控件 （A、 B 和 C） 以接收來自三個不同公司訊息。 若要讓每個主控件高度可用，您需要在兩部或以上的電腦中為每個主控件建立主控件執行個體。 請注意，您可以在一部電腦上擁有每個主控件的執行個體，而不會損失安全範圍、管理性或擴充性。  
  
 下圖顯示高度可用的三部電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與主機環境專用於接收不同公司的訊息。  
  
 ![向外擴充接收主控件](../technical-guides/media/04bd4234-dc71-49d8-b630-0643390b29f0.gif "04bd4234-dc71-49d8-b630-0643390b29f0")  
  
 若要以此組態提供高可用性，每部電腦都需執行三個主控件執行個體：三家公司的每一家各有一個執行個體。 每家公司的主控件執行個體都包含接收位置和管線以便和該公司通訊。 在一般的作業期間，只要您已完成必要的工作，向外延展前面的接收配接器，傳訊負載將分散於三個主控件執行個體每個主控件。 若一部電腦上的主控件執行個體失敗，在另外兩部電腦上執行的主控件執行個體會提供備援並維護服務的可用性。  
  
## <a name="scaling-out-isolated-receiving-hosts"></a>相應放大外掛式接收主控件  
 除了主控件執行個體，縮放比例和為接收主控件提供高可用性的程序也取決於您在您的部署中實作的特定配接器。 每個配接器都有通訊協定特有的特性，使得每個案例中的規劃和部署均不同。 不過，BizTalk Server 可讓您套用所有的配接器，主要是透過其他電腦和主控件執行個體的相同高可用性解決方案。  
  
 視要使用的特定通訊協定之不同，某些接收配接器需要其他機制，以便在多個主機電腦之間分散內送訊息以提供高可用性。 例如，使用 HTTP 或 SOAP 配接器 （亦稱為 Web 服務配接器） 的 BizTalk Server 解決方案都需要負載平衡器等網路負載平衡 (NLB) 來分散接收工作負載，如下圖所示。  
  
 ![向外擴充外掛式接收主控件](../technical-guides/media/cb38ec25-bfb0-4a55-8464-b7918b6fc746.gif "cb38ec25-bfb0-4a55-8464-b7918b6fc746")  
  
 如需有關在最常見的配接器的高可用性指導方針[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱 < 擴充 BizTalk Server 接收配接器 > 一節[Scaled-Out 接收主機](http://go.microsoft.com/fwlink/?LinkId=151283)(<http://go.microsoft.com/fwlink/?LinkId=151283>) 在 BizTalk 中Server 說明。  
  
## <a name="see-also"></a>另請參閱  
 [叢集接收主控件](../technical-guides/clustering-receiving-hosts.md)   
 [向外擴充處理主控件](../technical-guides/scaling-out-processing-hosts.md)   
 [向外擴充傳送主控件](../technical-guides/scaling-out-sending-hosts.md)