---
title: MQSeries 配接器的結構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, MQSeries adapters
- MQSeries adapters, architecture
ms.assetid: d25caf6a-3f93-4164-9c92-489b919a624d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6239b78f0b9bd2c44a314b7ba0ba6ace8f3b78e4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278494"
---
# <a name="structure-of-the-mqseries-adapter"></a>MQSeries 配接器的結構
MQSeries 配接器有兩個部分： 執行配接器[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 COM + 應用程式，MQSAgent、 下執行 MQSeries Server for Windows。 下圖顯示此關係。  
  
 ![MQSeries 配接器元件](../core/media/bts-dev-mqoverallstructure.gif "BTS_Dev_MQOverallStructure")  
  
 配接器與 MQSAgent 應用程式通訊。 然後 MQSAgent 應用程式與 MQSeries Server for Windows 通訊。 若您將 MQSeries Server for Windows 安裝在電腦上，可以將代理程式安裝在與配接器相同的電腦上。  
  
 配接器的傳送埠將訊息傳送至 MQSAgent。 MQSAgent 然後使用**MQPut**，將訊息傳送至 MQSeries 佇列管理員。  
  
 配接器的接收部分輪詢 MQSAgent，以查看是否有訊息。 訊息時，MQSAgent 會執行**MQGet**擷取訊息。 MQSAgent 從「佇列管理員」擷取訊息時，包含內定 3 秒的等待間隔。  
  
> [!NOTE]
>  您可以設定配接器的輪詢間隔。 當您將輪詢間隔設定為少於三秒時，等待間隔會設為輪詢間隔。  
  
 傳送和接收訊息動作都可能在交易中發生。 這讓配接器能夠回復資訊，也可能重試傳送或接收作業。 如需有關交易的詳細資訊，請參閱[MQSeries 配接器批次和交易處理](../core/mqseries-adapter-batching-and-transaction-handling.md)。  
  
 因為配接器是在一部以上的電腦運作，所以可能發生安全性問題。 有害的程式可能會模擬代理程式並擷取資料。 如需有關增強的保護代理程式與配接器的詳細資訊，請參閱[MQSeries 配接器安全性](../core/mqseries-adapter-security.md)。  
  
## <a name="see-also"></a>另請參閱  
 [MQSeries 配接器架構](../core/mqseries-adapter-architecture.md)   
 [何謂 MQSeries 配接器？](../core/what-is-the-mqseries-adapter.md)