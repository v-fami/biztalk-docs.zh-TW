---
title: 如何設定接收和傳送位置以及連接埠的 BAM WCF 攔截 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 501194dc-427a-4910-88c9-19cf47daeaad
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa77f39e8320c0d6598caaf5ea547592078774ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248438"
---
# <a name="how-to-configure-receive-and-send-locations-and-ports-for-bam-wcf-interception"></a>如何設定 BAM WCF 攔截的接收和傳送位置及連接埠
在這個程序中，您將在根據訊息內容決定路由 (CBR) 的情況下設定接收和傳送位置，以最直接的方式說明重要概念。 此處說明的概念適用於做為 [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] 服務公開的協調流程。  
  
## <a name="prerequisites"></a>必要條件  
 此程序假設您已經：  
  
-   修改 machince.config 檔案中所示[如何新增 BAM 攔截器行為至 Machine.config 檔](../core/how-to-add-the-bam-interceptor-behavior-to-the-machine-config-file.md)。  
  
-   建立 BizTalk Server 中所述的 WCF 配接器[如何建立 BizTalk Server WCF 配接器](../core/how-to-create-a-wcf-adapter-for-biztalk-server.md)。  
  
### <a name="to-configure-the-receive-and-send-locations"></a>若要設定接收和傳送位置  
  
1.  開啟 [BizTalk 管理主控台]。 若要這樣做，請按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  展開主控台樹狀目錄，找出 BizTalk 應用程式的 [接收位置] 節點。 按一下[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，按一下 [**應用程式**，按一下您在選取的應用程式[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務類型] 對話方塊，然後按一下**接收位置**。 與您所建立之接收位置相對應的新接收位置隨即出現， 並且處於停用狀態。  
  
3.  按兩下接收位置，以開啟**接收位置屬性**對話方塊方塊中，，然後選擇 Wcf-custom 傳輸類型。  
  
4.  按一下**設定** 按鈕以開啟**Wcf-custom 傳輸屬性** 對話方塊。  
  
5.  按一下**繫結**索引標籤上，選取您想要使用的繫結。  
  
6.  按一下**行為**索引標籤上，以滑鼠右鍵按一下 **[endpointbehavior]** 節點，然後再選取**加入擴充**。  
  
7.  選取 （這是您加入至 machine.config 檔案的副檔名） [bamendpointextension]，然後再按一下**確定**。  
  
     ![選取行為延伸模組畫面](../core/media/fe830d29-504e-465a-9316-b3f0db2dbc24.gif "fe830d29-504e-465a-9316-b3f0db2dbc24")  
  
8.  選取您剛才建立的延伸模組，輸入下列值，然後按**確定**:  
  
    |屬性|值|  
    |--------------|-----------|  
    |PollingIntervalSec|10|  
    |ConnectionString|ConnectionString： 整合式安全性 = SSPI;保存安全性資訊 = False; 初始目錄 = BAMPrimaryImport; 資料來源 =|  
  
9. 在**接收位置屬性**對話方塊中，選取**PassThruReceive**從**接收管線**下拉式清單，然後按一下**確定**.  
  
10. 啟用接收位置並重新整理管理主控台。 若狀態為已啟動，表示安裝成功。  
  
## <a name="see-also"></a>另請參閱  
 [設定 WCF 配接器攔截 BAM 資料](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)