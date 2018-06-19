---
title: 部分備份集 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9f15c0-4d31-4322-ac0a-8efdeed6f71e
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9740cb0f45d6bb46c13a95e50e4717ef142b164
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298158"
---
# <a name="partial-backup-sets"></a>部分備份集
當資料庫分別備份在來源系統上，該部分備份組中的結果，可能發生問題。 當發生這種情況時，Master.dbo.bts_LogShippingHistory 資料表會包含 0 **SetComplete**集中的所有記錄的資料行。  
  
 無法還原這些設定。 如此一來記錄備份組鏈結已中斷。 必須忽略集，以及所有記錄備份組之後，至下一個完整備份集。 還原作業會自動尋找下一個有效的完整備份組。 如果它找不到其中一個，它會失敗，並將還原的設定，才能修復目的地環境。  
  
 在大部分情況下來源系統會偵測部分備份組已發生，並會自動產生完整備份集，在下一次執行如果它被設定為執行這項操作。  
  
> [!NOTE]  
>  發生此問題最常見的原因是在目的系統上的檔案群組的磁碟空間不足。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解記錄傳送](../technical-guides/troubleshooting-log-shipping.md)