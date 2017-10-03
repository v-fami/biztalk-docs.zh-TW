---
title: "設定批次處理來改善配接器效能 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65589925-af94-45f1-b501-37c21618b2cf
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0dbee8e5b238af0a6dc7f15d54b85d85e0c4b26c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-batching-to-improve-adapter-performance"></a>設定批次處理來改善配接器效能
配接器處理批次的方式可能大幅影響效能。 因為每一個交易都有關聯的固定延遲，所以您應該嘗試將一個以上的作業結合成單一批次，讓交易的數目減至最少。  
  
 如果您提交訊息至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]批次，不會限制只會根據訊息計數的批次大小。 比方說，如果批次大小為二，而配接器取得四個訊息的大小 4 KB、 8 KB、 1 MB 和 5 MB，將會第一個批次大小的 12 KB 和第二個批次將是 6 MB 的大小。 由於 BizTalk 傳訊引擎會循序處理單一批次中的所有訊息，所以此範例中第二個批次的處理速度要比第一個批次緩慢許多， 這項的影響是降低的輸送量。  
  
 若要處理這個問題，我們建議您要批次處理為基礎的訊息計數和批次 （也就是以位元組為單位的批次大小） 中的位元組總數。 沒有任何最佳數目的位元組總數。 不過，在正常處理案例中，如果批次大小超過 1 MB，將會啟動遇到不佳的並行處理和輸送量。  
  
 配接器通常會處理在生產環境中的各種大小的訊息。 內送訊息的大小有可能會大大地改變。 如此一來，永遠使用訊息計數和總位元組數來建立批次。