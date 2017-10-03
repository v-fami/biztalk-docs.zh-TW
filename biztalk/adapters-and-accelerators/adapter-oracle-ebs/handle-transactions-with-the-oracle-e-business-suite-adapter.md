---
title: "處理交易與 Oracle E-business Suite 介面卡 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b443be9d-a93d-4836-8717-5ee9dad4442f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e00b31230760d1bb811b987c3b1a926bad803b6d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="handle-transactions-with-the-oracle-e-business-suite-adapter"></a>處理 Oracle E-business Suite 配接器的交易
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]不會啟動交易，以執行 Oracle E-business Suite 中的作業時發生。 相反地，配接器會執行作業使用配接器用戶端所提供的交易內容。 為了執行作業中使用交易[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須：  
  
-   啟用配接器用戶端中的交易。 例如，若要啟用交易中的[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]，您必須選取**Use Transaction**中核取方塊**交易**區域**訊息** 索引標籤WCF 自訂 」 或 「 Wcf-oracleebs 連接埠。  
  
-   值設定**UseAmbientTransaction**內容繫結至**True**配接器中。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
> [!IMPORTANT]
>  若要使用配接器執行 Oracle E-business Suite 中的交易，您必須安裝**Oracle Microsoft Transaction Server 服務**執行配接器的電腦上安裝 Oracle 用戶端時，元件用戶端。  
  
## <a name="transactions-in-the-outbound-operations"></a>在輸出作業中的交易  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]在單一交易中執行的輸出的作業。 複合作業，所有作業都都在單一交易，但使用不同的 ODP.NET 連線。 如需有關由顯示的輸出作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[配接器介面 Oracle E-business Suite 中繼資料的運作方式？](https://msdn.microsoft.com/library/dd788431.aspx)。  
  
## <a name="transactions-in-the-inbound-operations"></a>輸入的作業中的交易  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會公開下列兩個輸入的作業：  
  
-   **輪詢**： 輪詢陳述式和後輪詢陳述式 （如果有指定） 中執行的交易，而在不同交易中執行輪詢的資料的可用陳述式。 同樣地，輪詢陳述式後輪詢陳述式執行和使用相同的 ODP.NET 連接，而輪詢的資料可用陳述式使用不同的 ODP.NET 連線。  
  
-   **通知**： 通知作業使用單一 ODP.NET 連接在交易中執行。  
  
 如需有關由顯示輸入操作[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[配接器介面 Oracle E-business Suite 中繼資料的運作方式？](https://msdn.microsoft.com/library/dd788431.aspx)。  
  
## <a name="see-also"></a>另請參閱  
[瞭解 BizTalk Adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)