---
title: 定義資料庫的自動成長設定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dd86dd49-6505-4673-b413-d3af729dfca9
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d37bcce2d60167496bc55a12c65a488db17fceb
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
ms.locfileid: "29710785"
---
# <a name="define-auto-growth-settings-for-databases"></a>定義資料庫的自動成長設定
您應該將資料庫自動成長設 mb，而不是百分比，特別是針對 MessageBox 和 「 BizTalk 追蹤資料庫的固定數。 根據您的 BizTalk 應用程式和輸送量，MessageBox 與追蹤資料庫可以變得很大。 如果您將設定自動成長百分比，然後自動成長也很嚴重。  
  
## <a name="how-instant-file-initialization-works"></a>如何立即檔案初始化的運作方式  
 當 SQL Server 會增加檔案大小時，它必須先初始化新的空間，才能使用。 這是封鎖作業，包括新的空間中填入空白頁。 在 Windows 上的 SQL Server 支援立即檔案初始化。 」 這可大幅減少檔案成長作業的效能影響。 如需詳細資訊，請參閱[資料庫檔案初始化](https://docs.microsoft.com/sql/relational-databases/databases/database-instant-file-initialization)。 本主題概述必須採取以啟用立即檔案初始化的步驟。  
  
## <a name="enable-instant-file-initialization"></a>啟用立即檔案初始化  
 針對步驟啟用立即檔案初始化，請參閱[資料庫檔案初始化](https://docs.microsoft.com/sql/relational-databases/databases/database-instant-file-initialization)。 用於建立檔案群組，並將 BizTalk Server 資料庫資料表、 索引和記錄檔移到適當的檔案群組，請遵循建議[BizTalk 效能最佳化指南](../technical-guides/biztalk-server-2013-performance-optimization-guide.md)。 在理想情況下支援的檔案群組的檔案大小應該預先配置，並可能的話，請設定為靜態的大小。  
  
 如果是新系統，而且靜態的大小不已明確建立，然後設定檔案與**啟用自動成長**選項，並指定檔案的成長**以 mb 為單位**。 成長遞增值通常是不能大於 100 MB （適用於大型的檔案）、 10 MB （適用於中小型檔案） 或 1 MB （適用於小型檔案）。
