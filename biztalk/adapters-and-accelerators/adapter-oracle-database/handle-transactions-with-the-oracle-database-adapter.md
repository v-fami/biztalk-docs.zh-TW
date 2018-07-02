---
title: 使用 Oracle 資料庫配接器處理交易 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 971c2fba-640c-4ae5-9ab3-2d8227c1627d
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d94914c2f0f7bde91ea55032048e30232af60d02
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970703"
---
# <a name="handle-transactions-with-the-oracle-database-adapter"></a>使用 Oracle 資料庫配接器處理交易
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] 不會啟動交易時執行的 Oracle 資料庫上的作業。 相反地，配接器會執行使用配接器用戶端所提供的異動內容的作業。 若要執行作業在交易中使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須：  
  
-   啟用配接器用戶端中的交易。 例如，若要啟用 BizTalk Server 中的交易，您必須選取**Use Transaction**中的核取方塊**交易**區域**訊息**WCF 自訂 索引標籤或Wcf-oracledb 連接埠。  
  
-   設定的值**UseAmbientTransaction**屬性來繫結 **，則為 True**配接器中。 如需有關繫結屬性的詳細資訊，請參閱[Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
> [!IMPORTANT]
>  若要使用配接器執行的 Oracle 資料庫上的交易，您必須安裝**Oracle Microsoft Transaction Services Server**元件，同時執行配接器的電腦上安裝 Oracle 用戶端用戶端。  
  
## <a name="transactions-in-the-outbound-operations"></a>在輸出的作業中的交易  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]單一交易中執行輸出作業。 對於複合作業，所有作業將會在單一交易，但使用不同的 ODP.NET 連線。 如需詳細資訊，呈現的輸出作業的相關[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 配接器介面 Oracle 中繼資料的運作方式？](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx)。  
  
## <a name="transactions-in-the-inbound-operations"></a>輸入的作業中的交易  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會公開下列兩項輸入的作業：  
  
- **輪詢**： 輪詢陳述式和後輪詢陳述式 （如果有指定） 會在交易中執行，而不同的交易中執行輪詢的資料提供陳述式。 同樣地，輪詢陳述式後輪詢陳述式執行和使用相同的 ODP.NET 連線，而使用不同的 ODP.NET 連接 」 來執行 「 輪詢的資料提供陳述式。  
  
- **通知**： 通知作業中使用單一的 ODP.NET 連接的交易。  
  
  如需詳細資訊，呈現輸入作業的相關[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 配接器介面 Oracle 中繼資料的運作方式？](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Oracle Database 概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)