---
title: 保護應用程式 Oracle EBS |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76147120-57a8-4959-a0ff-77d04dee06a6
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9a7427d36ead6ba91e0d68b1080c9ab4f5155fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214998"
---
# <a name="secure-your-oracle-ebs-applications"></a>保護您的 Oracle EBS 應用程式
Oracle E-business 應用程式可以處理敏感性商務資訊，例如客戶帳戶詳細資料。 使用應用程式[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]來存取和修改這項資訊是在本機或分散式網路上可能會不小心公開以存取由未經授權的動作項目，除非工作所建立的保護，並保護期間的資料傳輸。 資料保護和安全性是通常視為以下列形式：  
  
-   *授權*控制存取資源，根據要求者的身分識別。  
  
-   *驗證*提供機制來驗證要求者的身分識別。  
  
-   *資料機密性*提供機制來保護透過加密資料的隱私權。  
  
-   *資料完整性*提供機制來數位簽署資料，讓接收者可以確認資料尚未改變傳輸中。  
  
 另一個值得注意的重要部分是使用者名稱密碼認證提供給[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 配接器會使用這些認證，以開啟 連線到 Oracle 資料庫。 這些認證可以提供在 連線 URI，不過，因為使用者名稱和密碼的純文字、[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]提供替代的方法可讓您以更安全的方式提供這些認證。  
  
 此章節的主題提供指導方針來協助您更安全的解決方案，開發[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  
  
