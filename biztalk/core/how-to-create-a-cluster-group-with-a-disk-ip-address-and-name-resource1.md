---
title: "如何建立叢集群組的磁碟，IP 位址，並命名 Resource1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b361f721-60db-485e-9ce3-48a6871ebd79
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63310706742ffcc10de5266dda7053da79fc04fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-cluster-group-with-a-disk-ip-address-and-name-resource"></a>如何使用磁碟、IP 位址及名稱資源建立叢集群組
為叢集[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]元件以及相依性能透過 NetBIOS，叢集網路上可供存取，**網路名稱**相同叢集群組中，必須建立資源。 叢集網路名稱資源可供存取，透過 TCP/IP 通訊協定， **IP 位址**相同叢集群組中，必須建立資源。 某些[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]相依性還必須使用叢集**實體磁碟**資源才能正確運作。 若要建立的叢集群組**實體磁碟**， **IP 位址**和**網路名稱**資源，請遵循下列步驟：  
  
### <a name="to-create-a-service-or-application-with-a-physical-disk-ip-address-and-network-name-resource"></a>若要建立與實體磁碟、 IP 位址和網路名稱資源的服務或應用程式  
  
1.  在 Windows 中，按一下 **啟動**，**程式**，**系統管理工具**，然後**容錯移轉叢集管理**啟動容錯移轉叢集管理程式。  
  
2.  容錯移轉所有的服務和應用程式執行容錯移轉叢集管理的叢集節點。 若要容錯移轉服務或應用程式，以滑鼠右鍵按一下服務或應用程式容錯移轉叢集管理的左窗格中，指向**將此服務或應用程式到另一個節點移動**按一下來選取目的地節點。  
  
    > [!NOTE]
    >  裝載執行中叢集資源的叢集節點就是所謂**active**節點。 裝載非執行中叢集資源的叢集節點就是所謂**被動**節點。  
  
3.  在左側窗格中，以滑鼠右鍵按一下**服務和應用程式**，按一下 **設定服務或應用程式**以啟動 高可用性精靈，然後按一下**下一步**.  
  
4.  按一下以選取**檔案伺服器**按一下**下一步**。  
  
    > [!NOTE]
    >  選取**檔案伺服器**此時會完成，因為直接的方法具有磁碟資源建立叢集群組。  
  
5.  在**用戶端存取點**高可用性精靈] 的頁面上，輸入唯一的網路名稱**名稱**方塊中，例如*BizTalkCluster*，輸入可用的 IP在解決**位址**，然後按一下 [**下一步**。  
  
6.  在**選取儲存體**頁面中，按一下以選取可用的磁碟資源，然後按一下**下一步**。  
  
7.  在**確認**頁面上，按一下**下一步**建立叢集群組。  
  
8.  在**摘要**頁面上，按一下**完成**。