---
title: 為 BizTalk 主控件提供高可用性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, MessageBox database
- planning, hosts
- hosts, high availability
- messages, routing
- deploying, high availability
- high availability, hosts
- hosts
- hosts, planning
- MessageBox database
ms.assetid: 9583b85c-7cad-4016-8065-5ca7de3f4359
caps.latest.revision: 47
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f964a8e170c2215c4abb2b6b5842f8fe0e159457
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271894"
---
# <a name="providing-high-availability-for-biztalk-hosts"></a>為 BizTalk 主控件提供高可用性
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 為處理高可用性提供很大的彈性，您可以策略性地讓邏輯主控件專用於執行特定部分的功能，例如，接收訊息、傳送訊息或處理協調流程。  
  
 BizTalk 主控件是 BizTalk Server 群組中的邏輯容器，可儲存 BizTalk Server 的項目，例如，配接器處理常式、接收位置 (包括管線)，以及協調流程。 您通常會將具有相似擴充需求的項目群組到特定的主控件中。 例如，您會將接收位置群組到「接收」主控件中、將傳送埠群組到「傳送」主控件中，以及將協調流程群組到「處理」主控件中。  
  
 在您建立主控件 (邏輯容器) 後，可以將主控件的執行個體設定為在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組中的實體 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上執行。 主控件執行個體會以 Windows 服務的形式在指定的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上執行。 雖然同一個 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上不能執行相同主控件的多個執行個體，但是您可以在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組中的不同 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上設定特定主控件的執行個體，以執行該主控件的多個執行個體。 您也可以在單一 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上執行多個不同主控件的執行個體。  
  
 BizTalk 主控件中所包含的項目可執行以下功能：  
  
-   **接收**在接收位置收取後，這些項目進行初始訊息的處理。 當主控件包含接收項目時 (例如接收位置或管線)，它將做為安全範圍，而訊息解碼和解密都發生在主控件的管線中。  
  
-   **傳送**會傳送至傳送埠之前，這些項目進行最終處理的訊息。 當主控件包含傳送項目時 (例如，傳送埠或管線)，主控件將做為安全範圍，而訊息簽章和加密都發生在主控件的管線中。  
  
-   **處理**這些項目會處理訊息的協調流程中指示為基礎。  
  
 雖然單一 BizTalk 主控件可以包含項目接收、 傳送和處理訊息，就是最佳做法來建立不同的主控件針對每個函式來建立安全性界限及更容易管理和延展性。 尤其，建議您使用不同的主控件來進行處理、接收/傳送作業，並將信任和非信任的項目分開。  
  
 例如，若您接收一個訊息、執行協調流程，並傳送十個訊息，您要將接收和傳送功能分成兩個獨立的主控件，因為傳送項目將會比接收項目多出十倍的流量。 若您接收一個訊息、執行協調流程，並傳送一個訊息，您可以將這些項目視為一個工作單位並將它們群組為單一主控件。 或者，您可以將這些作業分散到三個不同的主控件中，以提高效能和彈性。  
  
 BizTalk 主控件為下列其中一種，**同處理序**或**隔離**。 「內含式」主控件在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段程序內執行，而「外掛式」主控件則不在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段程序中執行。 下表列出每個主控件類型可能包含的項目。  
  
|**主機類型**|**邏輯容器**|  
|-------------------|-------------------------------|  
|內含式|-協調流程<br />配接器傳送處理常式<br />配接器接收處理常式，HTTP 和 SOAP 以外|  
|外掛式|HTTP 和 SOAP 接收處理常式|  
  
 如需主控件和主控件執行個體的詳細資訊，請參閱[管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)。  
  
 若要讓 BizTalk 主控件達到高可用性，您必須讓環境中的每個主控件均有兩個或以上的主控件執行個體 (放在兩部或更多部 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上)。 讓每個主控件均有不只一個主控件執行個體，可確保萬一某個主控件執行個體變得無法使用，其他執行該主控件之執行個體的電腦可以繼續提供有問題或失敗之主控件執行個體的功能，而使整個系統可以在最少中斷的情況下持續運作。  
  
## <a name="message-persistence"></a>訊息保存  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 高度依賴 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 以獲得高可用性，因為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的每個主控件都會將訊息保存到 MessageBox 資料庫`. 例如，當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收內送訊息時，在其他主控件擷取協調流程處理和傳送的訊息之前，接收主控件會將它保存到 MessageBox 資料庫。  
  
 若您的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 方案包含協調流程，則 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會將訊息路由至執行商務程序 (處理主控件) 的主控件，並在完成協調流程後，將訊息儲存到 MessageBox 資料庫。 傳送主控件接著會從 MessageBox 資料庫擷取訊息，再透過適當的傳送配接器將它傳送到外部應用程式。  
  
## <a name="separating-the-host-and-database-functions"></a>分隔主控件與資料庫功能  
 因為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會分隔資料與處理資料的主控件，所以為了建立高度可用的環境，您可以採取的步驟是將發生在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的主控件功能 (傳送、接收和處理) 與發生在 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 中的資料庫功能分開。 藉由分開這些功能，您可以針對處理主控件、傳送主控件、接收主控件和用於儲存資料的資料庫分開進行擴充。 執行階段和資料庫層是相關的，也就是說，若您增加 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦的數目，您可能需要增加執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的電腦數目以處理額外的負載。 不過，資料庫層與 BizTalk 層之間沒有直接的關係。 它們是兩個獨立層，您可以個別將它們向外擴充。  
  
 要讓主控件高度可用所需做的事與讓資料庫高度可用所需做的事是不同的。 下節說明您要讓接收、傳送和處理主控件高度可用所需做的事。 如需如何建立資料庫層級高可用性的詳細資訊，請參閱[的 BizTalk Server 資料庫提供高可用性](../core/providing-high-availability-for-biztalk-server-databases.md)。  
  
 針對 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 程序多於 SQL Server 程序的部署，您可以將多部 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦設定為使用同一部執行 SQL Server 的電腦。 此組態使用每部電腦上可用的資源。 例如，若 CPU 或記憶體使用率在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上很高 (超過 75%)，但是在執行 SQL Server 的電腦上很低 (低於 25%)，則可以將其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦納入以分散工作負載，並提升執行 SQL Server 的電腦的資源使用率。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [向外擴充接收主控件](../core/scaled-out-receiving-hosts.md)  
  
-   [向外延展處理主控件](../core/scaled-out-processing-hosts.md)  
  
-   [向外延展傳送主控件](../core/scaled-out-sending-hosts.md)  
  
-   [使用 Windows 伺服器叢集以提供高可用性的 BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)  
  
## <a name="see-also"></a>另請參閱  
 [為 BizTalk Server 資料庫提供高可用性](../core/providing-high-availability-for-biztalk-server-databases.md)   
 [企業單一登入的高可用性](../core/high-availability-for-enterprise-single-sign-on.md)