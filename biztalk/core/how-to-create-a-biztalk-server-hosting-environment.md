---
title: 如何建立 BizTalk Server 主控件環境 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- hosting environments, creating
- managing [hosts], hosting environments
- hosts, environments
- managing [hosts], creating
- creating, hosting environment
ms.assetid: 6f335139-1121-45ff-88da-5c626b8fff97
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba3829a2fecb32a191b7351833e975bf3770547d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013375"
---
# <a name="how-to-create-a-biztalk-server-hosting-environment"></a>如何建立 BizTalk Server 主控件環境
建立之前您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]裝載環境，請考慮下列建議：  

- **使用不同的主控件的信任和非信任的協調流程和接收處理常式**  

   任何在主控件中執行的項目 (例如，協調流程、管線、接收和傳送處理常式) 會以相同的識別來執行，而且可以存取該主控件的工作和擱置佇列。  

   若因為權限錯誤，造成訊息無法傳遞至協調流程，則訊息會放置在主控件的擱置佇列，也就是執行傳送程序 (接收管線或其他協調流程) 的位置。 不過，若協調流程和傳送程序 (例如，接收管線) 是在相同主控件執行，則協調流程仍可存取擱置佇列中的訊息。 若不信任的協調流程在信任的主控件上執行，可能會降低系統效能。  

   建議您在個別的主控件執行不信任的協調流程，並使用與您 BizTalk 群組中信任的主控件不同之服務帳戶。 如需將主控件指定為受信任，請參閱[如何修改主機內容](../core/how-to-modify-host-properties.md)。  

- **限制 BizTalk Server 資料庫中的資料庫和記錄檔的大小**  

   BizTalk MessageBox 資料庫和 BizTalk 追蹤資料庫的成長速度比其他[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 您應將經常更新這些資料庫，當作是備份和維護計劃的一部分。  

   根據預設，在資料表[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫沒有記錄大小限制。 在備份和維護計劃中，建議您限制記錄大小，以避免日誌過大而可能使用所有的磁碟空間。 如需管理追蹤資料庫大小的資訊，請參閱 <<c0> [ 封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)。  

- **使用 SQL Server 叢集**  

   若要提供高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，建議您叢集的 SQL server 其中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫會儲存。 若其中一個資料庫或 SQL Server 失敗，這樣便可將停機的可能性降至最低。 如需有關 SQL Server 叢集的詳細資訊，請參閱 < 容錯移轉叢集架構 > SQL Server 線上叢書 》 中。  

## <a name="prerequisites"></a>必要條件  
 以下是執行此主題中之程序的必要條件：  

- 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  

- 下列程序中的指示假設您已安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]完整安裝選項。 如果您未安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用完整安裝選項時，某些步驟 1 中所列的系統管理物件可能不在您的系統上。  

### <a name="to-create-a-biztalk-server-hosting-environment"></a>建立 BizTalk Server 主控件環境  

1. 使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態，以建立新的 BizTalk 群組。 如需建立新[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組，請參閱[使用 BizTalk Server 組態的設定群組](http://msdn.microsoft.com/library/16beb7bb-091c-4056-8622-cc79c95186e9)。  

    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態會建立下列管理物件：  


   |                   管理物件                    |                                                                                                                                                                                                                                       描述                                                                                                                                                                                                                                       |
   |------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |      **BizTalk 管理**資料庫 (BizTalkMgmtDb)       |                                                                                                                                                                    此資料庫是所有的中央中繼資訊存放區[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s。                                                                                                                                                                     |
   |     **BizTalk MessageBox**資料庫 (BizTalkMsgBoxDb)      |           這個資料庫儲存了訂閱述詞。 它是主應用程式平台，並保留每個佇列和狀態資料表[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主應用程式。 MessageBox 資料庫也儲存訊息及訊息屬性。 如需 MessageBox 資料庫的資訊，包括新增其他 MessageBox 資料庫，請參閱[管理 MessageBox 資料庫](../core/managing-messagebox-databases.md)。           |
   |                         **Server**                         | 這是在其上的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]已安裝和設定，以及主控件執行個體執行所在的位置。 您是從在伺服器上建立的主控件，而建立主控件執行個體。 如需建立主控件的詳細資訊，請參閱[如何建立新的主控件](../core/how-to-create-a-new-host.md)。 如需建立主控件執行個體的資訊，請參閱[如何新增主控件執行個體](../core/how-to-add-a-host-instance.md)。 |
   |     **BAM 主要匯入**資料庫 (BAMPrimaryImport)     |                                                                                                                                                                                                這是「商務活動監控」工具收集追蹤資料的資料庫。                                                                                                                                                                                                 |
   |       **規則引擎**資料庫 (BizTalkRuleEngineDb)       |                                                                                                                                                                                       這個資料庫是原則、規則和詞彙的儲存機制，可以在商務規則中進行資料參考。                                                                                                                                                                                        |
   |        **BizTalk 追蹤**資料庫 (BizTalkDTADb)        |                                                                                                                                                       此資料庫儲存商務和狀況監控的資料，追蹤[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]追蹤引擎。                                                                                                                                                       |
   |                  **SSO**資料庫 (SSODB)                  |                                                                                                                                                                                                                      此資料庫儲存認證資訊。                                                                                                                                                                                                                       |
   |   **內含式主控件**與對應的主控件執行個體    |                                                                                                                                                                        內含式主控件會在內部運作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理序空間。                                                                                                                                                                        |
   |    **外掛式主控件**與對應的主控件執行個體     |                                                                                                                                                                       外掛式主控件運作之外[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝。                                                                                                                                                                        |
   | HTTP/S、BizTalk 訊息佇列、File、SMTP、SOAP 和 SQL |                                                                                                                                                                   組態精靈會建立做為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 一部分的配接器。                                                                                                                                                                    |


2. 使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台或 WMI，將元件加入您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]所需的環境。 若要擴充您的解決方案、新增 MessageBox 資料庫、主控件和服務：  

3. 使用「BizTalk 管理主控台」或 WMI，在對應的伺服器建立主控件執行個體。 這個步驟會決定哪一部伺服器上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會執行。 隨著企業變更的需求，您可以新增伺服器、移除伺服器以及變更伺服器與主控件對應。  

## <a name="see-also"></a>另請參閱  
 [管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)   
 [主機](../core/hosts.md)   
 [主控件執行個體](../core/host-instances.md)