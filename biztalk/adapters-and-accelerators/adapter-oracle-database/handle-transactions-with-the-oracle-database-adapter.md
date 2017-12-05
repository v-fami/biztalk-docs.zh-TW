---
title: "使用 Oracle 資料庫配接器處理交易 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 971c2fba-640c-4ae5-9ab3-2d8227c1627d
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5072a49c9edc5dc8ce03ec819d6042b640b94a47
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="handle-transactions-with-the-oracle-database-adapter"></a>使用 Oracle 資料庫配接器處理交易
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]不會啟動交易時執行的 Oracle 資料庫上的作業。 相反地，配接器會執行作業使用配接器用戶端所提供的交易內容。 為了執行作業中使用交易[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須：  
  
-   啟用配接器用戶端中的交易。 例如，若要啟用 BizTalk Server 中的交易，您必須選取**Use Transaction**中核取方塊**交易**區域**訊息**WCF 自訂 索引標籤或Wcf-oracledb 連接埠。  
  
-   值設定**UseAmbientTransaction**內容繫結至**True**配接器中。 如需繫結屬性的詳細資訊，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
> [!IMPORTANT]
>  若要使用配接器的 Oracle 資料庫上執行交易，您必須安裝**Oracle Microsoft Transaction Server 服務**執行配接器的電腦上安裝 Oracle 用戶端時，元件用戶端。  
  
## <a name="transactions-in-the-outbound-operations"></a>在輸出作業中的交易  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在單一交易中執行的輸出的作業。 複合作業，所有作業都都在單一交易，但使用不同的 ODP.NET 連線。 如需有關由顯示的輸出作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[配接器介面 Oracle 中繼資料的運作方式？](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx)。  
  
## <a name="transactions-in-the-inbound-operations"></a>輸入的作業中的交易  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會公開下列兩個輸入的作業：  
  
-   **輪詢**： 輪詢陳述式和後輪詢陳述式 （如果有指定） 中執行的交易，而在不同交易中執行輪詢的資料的可用陳述式。 同樣地，輪詢陳述式後輪詢陳述式執行和使用相同的 ODP.NET 連接，而輪詢的資料可用陳述式使用不同的 ODP.NET 連線。  
  
-   **通知**： 通知作業使用單一 ODP.NET 連接在交易中執行。  
  
 如需有關由顯示輸入操作[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[配接器介面 Oracle 中繼資料的運作方式？](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx)。  
  
## <a name="see-also"></a>請參閱  
 [BizTalk Adapter for Oracle Database 概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)