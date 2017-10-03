---
title: "步驟 1： 設定檔案接收位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df591263-964a-4ad8-bc3a-a553de8dae4f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78f8bccc187bf310b8426fc3d5fee36add44a9f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-a-file-receive-location"></a>步驟 1： 設定檔案接收位置
本主題中，您可以設定讓檔案接收位置使用拖放到檔案資料夾，即可叫用傳送埠的虛擬要求訊息。  
  
> [!NOTE]
>  在本教學課程的步驟假設您使用預設的應用程式 (**BizTalk Application 1**) 若要建立方案。 您也可以建立另一個應用程式，並在任何該應用程式執行相同的步驟。  
  
### <a name="to-configure-a-file-receive-location"></a>若要設定 FILE 接收位置  
  
1.  從 BizTalk Server 管理主控台，在**BizTalk Application 1** ] 節點，以滑鼠右鍵按一下**接收埠**，指向**新增**，然後按一下 [ **單向接收埠**。  
  
2.  在 [一般] 索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**ReceivePortRestAzureMarketPlace**。|  
    |**啟用失敗訊息的路由**|(清除)|  
  
3.  按一下**接收位置**，然後按一下 **新增**。  
  
4.  從 [Receive Location1 - 接收位置屬性] 中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**ReceiveLocationAzureMarketPlace**。|  
    |**型別**|選取**檔案**。|  
    |**接收處理常式**|選取 **[BizTalkServerApplication]**。|  
    |**接收管線**|選取**PassThruReceive**。|  
  
5.  按一下**設定**。  
  
6.  從 [檔案傳輸屬性] 中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**接收資料夾**|輸入您將放置虛擬要求訊息的位置。|  
    |**檔案名稱**|保留`*.xml`|  
  
7.  按一下**確定**直到結束所有對話方塊為止。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 5： 叫用 REST 介面使用 BizTalk Server](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)