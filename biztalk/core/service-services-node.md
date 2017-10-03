---
title: "服務 （服務節點） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Service node [binding file]
ms.assetid: 19e977b4-55bd-453f-9053-5590b9553b07
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 834555f43620d428d18a04938e18612793b2ab51
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="service-services-node"></a>服務 (服務節點)
繫結檔案的 [服務] 節點，包含與該繫結檔案一起匯出之服務的相關資訊。 服務節點也包含一些描述與服務關聯之連接埠和角色的節點，以及一個描述與服務關聯之主控件的節點。  
  
## <a name="nodes-in-the-service-node"></a>服務節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|名稱|Attribute|xs:string|指定服務的名稱。|Required|預設值：空白|  
|State|Attribute|ServiceRefState (SimpleType)|指定服務的狀態。|Required|預設值： Default<br /><br /> 可能的值包括：<br /><br /> 預設<br />-取消登錄<br />登記<br />啟動|  
|TrackingOption|Attribute|OrchestrationTrackingTypes (SimpleType)|指定服務的訊息追蹤選項。|Required|預設值：無<br /><br /> 可能的值包括用於[Microsoft.BizTalk.ExplorerOM.OrchestrationTrackingTypes](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.orchestrationtrackingtypes.aspx)列舉型別。|  
|Description|Attribute|xs:string|指定服務的描述。|不需要|預設值：空白|  
|[連接埠](../core/ports-service-node.md)|記錄|ArrayOfServicePortRef (ComplexType)|繫結至服務之連接埠的容器節點。|不需要|預設值：無|  
|[角色](../core/roles-service-node.md)|記錄|ArrayOfRoleRef (ComplexType)|繫結至服務之角色的容器節點。|不需要|預設值：無|  
|[主機](../core/host-service-node.md)|記錄|HostRef (ComplexType)|繫結至服務之主控件的容器節點。|Required|預設值：無|