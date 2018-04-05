---
title: BindingInfo 節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BindingInfo node [binding file]
ms.assetid: a71d100c-cf8b-4a54-b239-ee0ca2d8148c
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3dc15cbfe4bb3a98e17a894c5a763c0ca18bdcb3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bindinginfo-node"></a>BindingInfo 節點
**BindingInfo**繫結檔案節點繫結檔案的根節點，並包含適用於所有繫結檔案中的項目，以及繫結檔案所匯出 BizTalk Server 相關資訊從。  
  
## <a name="nodes-in-the-bindinginfo-node"></a>BindingInfo 節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|組件|Attribute|xs:string|指定當建立繫結檔案時使用之 Microsoft.BizTalk.Deployment dll 的資訊。 包含這個組件的 Version、Culture 和 PublicKeyToken 等屬性 (以逗號分隔)。|Required|預設值： **"Microsoft.BizTalk.Deployment，Version = 3.0.1.0，Culture = neutral，PublicKeyToken = 31bf3856ad364e35 」**|  
|Version|Attribute|xs:string|指定產生繫結檔案所使用的 BizTalk Server 版本。|Required|預設值： **3.5.1.0**|  
|BindingStatus|Attribute|BindingState (SimpleType)|指定與繫結檔案一起匯出之成品的繫結狀態。|Required|預設值：無<br /><br /> 有效值：<br /><br /> -不明<br />-NoBindings<br />-未繫結<br />-PartiallyBound<br />-FullyBound|  
|BoundEndpoints|Attribute|xs:int|指定繫結檔案中繫結端點的數目。|Required|預設值： **0**|  
|TotalEndpoints|Attribute|xs:int|指定繫結檔案中端點的總數。|Required|預設值： **0**|  
|Description|元素|xs:string|指定繫結檔案之 BindingInfo 區段的文字描述。|不需要|預設值：空白|  
|時間戳記|元素|xs:dateTime|指定繫結檔案的匯出時間。|Required|預設值：匯出繫結檔案時 BizTalk Server 上的時間。|  
|[ModuleRefCollection 節點](../core/modulerefcollection-node.md)|記錄|ArrayOfModuleRef (ComplexType)|與此繫結檔案一起匯出之 .NET 組件的容器節點。|不需要|預設值：無|  
|[SendPortCollection 節點](../core/sendportcollection-node.md)|記錄|ArrayOfSendPort (ComplexType)|與此繫結檔案一起匯出之傳送埠的容器節點。|不需要|預設值：無|  
|[DistributionListCollection 節點](../core/distributionlistcollection-node.md)|記錄|ArrayOfDistributionList (ComplexType)|與此繫結檔案一起匯出之通訊群組清單的容器節點。|不需要|預設值：無|  
|[ReceivePortCollection 節點](../core/receiveportcollection-node.md)|記錄|ArrayOfReceivePort (ComplexType)|與此繫結檔案一起匯出之接收埠的容器節點。|不需要|預設值：無|  
  
 下列程式碼示範用於繫結檔案中 BindingInfo 節點內的 XML 格式：  
  
```  
<BindingInfo xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
Assembly="Microsoft.BizTalk.Deployment, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
Version="3.5.1.0" BindingStatus="FullyBound"   
BoundEndpoints="12"   
TotalEndpoints="12">  
<Description/>  
<Timestamp>2005-08-23T16:27:40.5948205-07:00</Timestamp>  
```  
  
## <a name="see-also"></a>另請參閱  
 [自訂繫結檔案](../core/customizing-binding-files.md)