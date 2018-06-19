---
title: 如何設定整合閘道和 HTTP 輸出連接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Integration Gateway
- gateway nodes, creating
- HTTP Output Connector
ms.assetid: a02ee533-07a8-42fa-a72a-7e5359b18f40
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acfa52be85a664432af95af0ca292e9cc394c6ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247918"
---
# <a name="how-to-configure-the-integration-gateway-and-http-output-connector"></a>如何設定整合閘道和 HTTP 輸出連接器
依照下列步驟設定「整合閘道」和「HTTP 輸出連接器」。  
  
### <a name="to-create-and-configure-a-new-gateway-node"></a>若要建立和設定新的閘道節點  
  
1.  在 Web 瀏覽器中開啟 PeopleSoft 應用程式。  
  
2.  找出**PeopleTools**，選取**Integration Broker**，然後選取**閘道**。  
  
3.  在**搜尋依據**欄位中，輸入`LOCAL`，然後按一下 **搜尋**。  
  
     ![](../core/media/psadapter-31-task-gatewaysearch.gif "PSAdapter_31_Task_GatewaySearch")  
  
4.  輸入`machine-name/PSIGW/PeopleSoftListeningConnector`到**Gateway URL**項目。  
  
     ![](../core/media/psadapter-32-task-gatewayurl.gif "PSAdapter_32_Task_GatewayURL")  
  
5.  按一下**重新整理**，然後按一下 **儲存**。  
  
6.  按一下**屬性**連結**HTTPTARGET**若要檢視屬性/值組合，該識別碼。  
  
     您可以在此或在 [Node Definition] 設定 URL。 在本討論中，請在 Node 層級設定 URL。  
  
     ![](../core/media/psadapter-33-task-gatewaynodelevel.gif "PSAdapter_33_Task_GatewayNodeLevel")  
  
## <a name="see-also"></a>另請參閱  
 [建立 PeopleSoft HTTP 主控件和連接埠](../core/creating-a-peoplesoft-http-host-and-port.md)