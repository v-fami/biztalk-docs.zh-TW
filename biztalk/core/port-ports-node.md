---
title: 連接埠 （連接埠節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Port node [binding file]
ms.assetid: 6c9a3e5f-0b3c-40f8-9a8d-5a83bd559021
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01a808f4415019ba48deb1b3b80ad8aae9e1db04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="port-ports-node"></a>連接埠 (連接埠節點)
繫結檔案的連接埠節點，包含與該繫結檔案一起匯出之服務所繫結連接埠或通訊群組清單的相關特定資訊。  
  
> [!NOTE]
>  通訊群組清單在 BizTalk Server「管理主控台」中也稱為傳送埠群組。  
  
## <a name="nodes-in-the-port-node"></a>連接埠節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|名稱|Attribute|xs:string|指定連接埠的名稱。|不需要|預設值：空白|  
|Modifier|Attribute|xs:int|指定連接埠的型別修飾詞。|Required|預設值：無<br /><br /> 可能的值包括用於[Microsoft.BizTalk.ExplorerOM.PortModifier](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.portmodifier.aspx)列舉型別。|  
|BindingOption|Attribute|xs:int|定義連接埠的繫結類型。|Required|預設值：無<br /><br /> 可能的值包括用於[Microsoft.BizTalk.ExplorerOM.BindingType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.bindingtype.aspx)列舉型別。|  
|[SendPortRef](../core/sendportref-port-node.md)|記錄|SendPortRef (ComplexType)|服務所參考之傳送埠的容器節點。|不需要|預設值：空白|  
|[DistributionListRef](../core/distributionlistref-port-node.md)|記錄|DistributionListRef (ComplexType)|服務所參考之通訊群組清單的容器節點。|不需要|預設值：空白|  
|[ReceivePortRef](../core/receiveportref-port-node.md)|記錄|ReceivePortRef (ComplexType)|服務所參考之接收埠的容器節點。|不需要|預設值：空白|