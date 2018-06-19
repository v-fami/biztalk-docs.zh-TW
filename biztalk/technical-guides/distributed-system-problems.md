---
title: 分散式系統問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 287b0adb-d5f9-4e47-80f8-0ba5d90c7864
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24abe471a66e8bc0724ad731388c5a0e7c07b573
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297750"
---
# <a name="distributed-system-problems"></a>分散式的系統問題
分散式的目的系統中的還原作業並不知道的錯誤或其他電腦上的問題。 例如，假設電腦 A 正在還原 BizTalk 管理資料庫和 BizTalk 追蹤資料庫，而且電腦 B 正在還原 BizTalk MessageBox 資料庫。 這兩部電腦已成功還原備份組 1 至 25。 設定 26，不過，有損毀的記錄備份檔案的 BizTalk MessageBox 資料庫。 電腦 A 正確還原其資料庫，但電腦 B 無法還原損毀的檔案。  
  
 在此情況下，請在來源系統上強制進行完整備份。 接續上例，假設已診斷的問題，並建立完整備份組 35。 直到它看到完整備份集 35 及後續的記錄備份組 （請記住，就必須一律是一組一個後續的完整記錄備份要還原的 36 電腦 A 則還原集 26 到 34，因為它並不知道電腦 B 的電腦上的問題將會失敗d) 中。 集合 35 及 36 到達時在電腦 B 上，它將會修復使用 35 本身。 修復完成後，電腦 A 和 B 會同步。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解記錄傳送](../technical-guides/troubleshooting-log-shipping.md)