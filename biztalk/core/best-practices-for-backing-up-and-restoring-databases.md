---
title: "備份和還原資料庫的最佳作法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices, maintaining
- restoring, best practices
- best practices, backing up
- backing up, restoring
- backing up, best practices
- maintaining, best practices
- best practices, restoring
ms.assetid: 649ca56b-3cc1-49ad-9f74-ba1521e65ee1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2543f09c5118e58bd18ea2add113811fb733d884
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-backing-up-and-restoring-databases"></a>備份和還原資料庫的最佳作法
請檢視下列最佳作法，以協助確保您可以備份和還原 BizTalk Server 資料庫。  
  
-   **開發備份和還原策略，並加以測試。**  
  
     如果擁有好的計畫，當您的資料因為硬體失敗而遺失時，便可以快速地還原。  
  
-   **管理磁碟空間和封存先前的備份檔案。**  
  
     備份 BizTalk Server 工作不會刪除過期的備份檔案，所以您必須管理那些備份檔案以回收磁碟空間。 在為資料庫建立新的完整備份後，您應該將過期的備份檔案移動到封存儲存裝置以回收主要磁碟上的空間。  
  
-   **不要在同一部電腦或您要備份的磁碟上儲存備份。**  
  
     您應該為備份指定與原始資料所在之電腦不同的電腦或磁碟。 否則，當硬體失敗時，您將會遺失所有的資料。  
  
-   **保留複本。**  
  
     至少保留三份媒體的複本。 保留至少一個異地適當受控制的環境。  
  
-   **執行試驗。**  
  
     一個月至少執行一次試驗復原，以確認您的檔案已適當備份。 試驗復原可以揭露您在驗證軟體是否正常運作時沒有出現的硬體問題。 不要等到您的硬碟失敗時，才嘗試是否可以還原您的系統和資料庫。  
  
-   **保護裝置和媒體。**  
  
     請同時保護儲存裝置和備份媒體。 可能有人會藉由將資料還原到另一個自己是系統管理員的伺服器，從偷來的媒體存取資料。  
  
-   **監控備份和還原程序。**  
  
     為確保備份和還原程序成功，您應該監控用來備份和還原 BizTalk Server 的 SQL Server Agent 作業。  
  
## <a name="see-also"></a>另請參閱  
 [備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-the-biztalk-server-databases.md)