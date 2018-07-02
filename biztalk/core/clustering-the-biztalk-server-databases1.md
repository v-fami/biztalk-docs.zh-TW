---
title: 叢集 BizTalk Server Databases1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- clustering, how to
- clustering, SQL Servers
- SQL Server, clustering
- BizTalk Server Configuration Wizard
- high availability, databases
- clustering, BizTalk Server Configuration Wizard
- clustering, databases
- clustering, prerequisites
ms.assetid: 9a1ed843-483b-4a56-961b-bc6801a07b64
caps.latest.revision: 32
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8a74f78098092f07b47e08b8f260d61129c739e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976671"
---
# <a name="clustering-the-biztalk-server-databases"></a>叢集 BizTalk Server 資料庫
本節提供部署具有高可用性之 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 解決方案的指導方針。 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫會變成無法使用，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境將無法正確運作。 若要提供高可用性，您可以建立適用於 Microsoft SQL Server 叢集[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，如下圖所示。  
  
 ![BizTalk Server 資料庫層](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")  
  
 若要提供高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，您必須擁有至少兩部電腦正在執行 SQL Server 和共用的磁碟陣列，以使用的 Windows Server 容錯移轉叢集。  
  
## <a name="procedures-for-clustering-the-databases"></a>叢集資料庫的程序  
  
#### <a name="before-you-start"></a>開始之前  
  
1. 當您建立網域群組的 BizTalk Server 環境時，您必須建立 Active Directory 網域全域群組。  
  
2. 安裝及設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之前，請先設定 SQL Server 叢集。 如需叢集 SQL Server 的詳細資訊，請參閱[Alwayson 容錯移轉叢集執行個體](https://technet.microsoft.com/library/ms189134.aspx)。  
  
3. 若您也要叢集主要密碼伺服器，請先設定該伺服器。 如需高可用性的企業單一登入，請參閱[高可用性的企業單一登入](../core/high-availability-for-enterprise-single-sign-on.md)。  
  
#### <a name="to-run-the-biztalk-server-configuration-wizard"></a>若要執行 BizTalk Server 組態精靈  
  
1. 在執行階段伺服器上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
2. 啟動 BizTalk 組態程式。 按一下 **開始**，指向**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 組態**。  
  
3. 請依照下列中的步驟[匯入和匯出 BizTalk Server 組態](../install-and-config-guides/import-and-export-biztalk-server-configuration.md)套用自訂組態。 若要指定 BizTalk 資料庫的 SQL Server 叢集，請輸入中的 SQL Server 叢集名稱**資料庫**對話方塊中的 「 組態 」 程式中所述**編輯資料庫**區段本主題中。  
  
4. 完成 BizTalk Server 組態中的指示[設定 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [建立高可用性的 BizTalk Server 環境](../core/creating-a-highly-available-biztalk-server-environment.md)