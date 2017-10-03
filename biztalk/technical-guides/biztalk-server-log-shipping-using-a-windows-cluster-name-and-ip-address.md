---
title: "BizTalk Server 記錄傳送使用 Windows 叢集名稱和 IP 位址 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82ef6908-6009-4d06-8315-0bc85a0aad18
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8619ea6c4eea3eefee5b86282a29e0165d0fb074
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-log-shipping-using-a-windows-cluster-name-and-ip-address"></a>BizTalk Server 記錄傳送使用 Windows 叢集名稱和 IP 位址
可簡化[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用兩個執行個體的記錄傳送[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集中，為來源和目的地伺服器中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送案例。 然後，萬一嚴重損壞修復事件發生資料庫復原已簡化藉由只切換的名稱和叢集相關聯的 IP 位址資源[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體，如下所述。 使用這個方式時無須執行 UpdateDatabase.vbs 指令碼，如本主題所述[如何還原資料庫中 「 備份 BizTalk Server 」 工作](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)因為資料庫名稱不會變更。  
  
> [!NOTE]  
>  若要增加的叢集容錯[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體，叢集[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]應該地理分隔執行個體。  
  
### <a name="to-implement-biztalk-server-log-shipping-using-a-windows-server-cluster-name-and-ip-address-resource"></a>為了實作 BizTalk Server 記錄傳送，並使用 Windows Server 叢集名稱和 IP 位址資源  
  
1.  停止生產環境 BizTalk 伺服器。  
  
2.  執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送還原至次要資料庫[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集。  
  
3.  請依照下列主題中所述的步驟[設定 BizTalk Server 記錄傳送](../technical-guides/configuring-biztalk-server-log-shipping.md)重新設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送，讓次要[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集執行個體現在是來源群組和主要[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集執行個體現在是目的地群組。  
  
4.  停止 IP 和網路名稱資源的主要 PublicSQLClustername[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集執行個體。  
  
5.  設定並啟動 PublicSQLClustername IP 和網路名稱叢集資源在次要複本上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集執行個體。  
  
6.  啟動實際 BizTalk 伺服器。  
  
7.  確認記錄傳送還原。  
  
8.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]相關將生產站台上的服務。  
  
 執行這些步驟之後，BizTalk 群組指向次要[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集執行個體，如下圖所示。  
  
 下圖說明如何設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送所使用的兩個叢集執行個體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和移動叢集的名稱和 IP 位址資源。  
  
 ![BizTalk 記錄傳送使用叢集名稱和 IP](../technical-guides/media/5055689e-c26b-4077-a531-74a50fec1393.gif "5055689e-c26b-4077-a531-74a50fec1393")  
  
 **使用 Windows Server 叢集名稱和 IP 位址資源的 BizTalk Server 記錄傳送實作**  
  
## <a name="see-also"></a>另請參閱  
 [資料庫的高可用性](../technical-guides/high-availability-for-databases.md)   
 [設定 BizTalk Server 記錄傳送](../technical-guides/configuring-biztalk-server-log-shipping.md)   
 [如何還原 「 備份 BizTalk Server 」 工作中的資料庫](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)