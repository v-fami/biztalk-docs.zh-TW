---
title: SecondaryTransport （SendPort 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SecondaryTransport node [binding file]
ms.assetid: e4924f63-dd5f-4437-a661-09f12c5d6da6
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2f988ccb7cd24187d595b2ef8315ee51fa6aae5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271302"
---
# <a name="secondarytransport-sendport-node"></a>SecondaryTransport (傳送埠節點)
[傳送埠] 節點的 [SecondaryTransport] 節點，針對繫結至繫結檔案所匯出之傳送埠的次要傳輸而提供特定資訊。 如果有指定次要傳輸，則在耗盡主要傳輸的所有重試嘗試時便會使用次要傳輸。  
  
## <a name="nodes-in-the-secondarytransport-node"></a>SecondaryTransport 節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|位址|元素|xs:string|指定傳輸的位址 (或 URI)。|不需要|預設值：空白|  
|[TransportType （SecondaryTransport 節點）](../core/transporttype-secondarytransport-node.md)|記錄|ProtocolType (ComplexType)|指定傳輸類型，這也是用於此傳輸的配接器名稱。|不需要|預設值：無|  
|TransportTypeData|元素|xs:string|指定特定於配接器的組態資訊。|不需要|預設值：空白<br /><br /> 請參閱[整合式 BizTalk 配接器的組態屬性](../core/configuration-properties-for-integrated-biztalk-adapters.md)的配接器特定資訊可以儲存這個字串中的屬性。|  
|RetryCount|元素|xs:int|指定用於傳輸的配接器重試次數。|Required|預設值：無|  
|RetryInterval|元素|xs:int|指定用於傳輸的配接器重試間隔 (以分鐘為單位)。|Required|預設值：無|  
|ServiceWindowEnabled|元素|xs:boolean|指定是否已針對用於傳輸的配接器啟用服務窗口。|Required|預設值：無<br /><br /> 設定為**true**如果已啟用服務窗口，否則設為**false**。|  
|FromTime|元素|xs:dateTime|指定服務窗口的開始時間。|Required|預設值：無|  
|ToTime|元素|xs:dateTime|指定服務窗口的結束時間。|Required|預設值：無|  
|Primary|元素|xs:boolean|指定用於傳輸的配接器是否為主配接器。|Required|預設值：無<br /><br /> 設定為**true**如果主要用於傳輸的配接器，否則設為**false**。|  
|OrderedDelivery|元素|xs:boolean|指定用於傳輸的配接器是否會以排序的方式來傳送訊息。|Required|預設值：無<br /><br /> 設定為**true**傳輸方式是在順序中傳送訊息，否則設為**false**。|  
|DeliveryNotification|元素|xs:int|指定用於傳輸的配接器是否會傳回傳遞通知，指出傳輸成功。|Required|預設值：無<br /><br /> 設定為**true**傳遞通知，否則設為**false**。|  
|[SendHandler](../core/sendhandler-secondarytransport-node.md)|記錄|SendHandlerRef (ComplexType)|指定用於傳輸配接器的傳送處理常式。|Required|預設值：無|