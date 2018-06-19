---
title: SQLEXECUTE 操作 Oracle 資料庫中的 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DML
- data manipulation language
- operations, DML
- SQLEXECUTE
ms.assetid: d7f881e4-c668-4f8e-b08a-ea6614b65910
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ac8d5c8284e1f273d4b9aef17e79e25636dc581
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215614"
---
# <a name="sqlexecute-operation-in-oracle-database"></a>SQLEXECUTE 操作 Oracle 資料庫中
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現一組標準的 Oracle 資料庫成品上的作業。 藉由使用這些作業，您可以呼叫之類的 Oracle 函式或程序，或執行基本 SQL 資料操作語言 (DML) 作業在資料表上。 不過，有可能會由您的商務邏輯驅動的案例需要您執行作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]並不會出現。 例如，您可能想要：  
  
-   對資料庫成品，便不會顯示所執行作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; 例如，取得 CURVAL 或 NEXTVAL 的 Oracle 序列。  
  
-   執行資料定義語言作業;例如，建立資料表。  
  
-   在未出現在設計階段; 資料庫成品上執行作業比方說，更新您的商務邏輯所建立的暫存資料表中的記錄。  
  
-   更複雜 DML 資料表上執行作業比作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]呈現; 例如，執行查詢，包括聯結子句。  
  
 這類情況下，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]呈現 SQLEXECUTE 操作。 SQLEXECUTE 操作中，會顯示在根節點 （/） 下**選取類別目錄**窗格[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。  
  
 藉由使用 SQLEXECUTE 操作，您可以在 Oracle 資料庫上執行參數化的 SQL 陳述式。 SQLEXECUTE 作業支援的參數集可讓您執行相同的 SQL 陳述式，一次針對每組所組成的輸入的參數區塊。 SQLEXECUTE 操作傳回泛型的記錄組中的 SQL 陳述式的結果。  
  
> [!NOTE]
>  您可以傳遞 IN 與 IN OUT 參數的程序、 函數和 SQLEXECUTE 操作中的封裝。 叫用的成品將使用 Oracle 資料庫上提供的參數來執行不過，SQLEXECUTE 作業不會傳回的 OUT 值及 IN OUT 參數，用戶端。 如果您想要叫用程序、 函數或封裝，我們建議您這麼做叫用的專用的作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開 （expose) 這些 Oracle 成品。  
  
 如需詳細資訊：  
  
-   使用執行 SQLEXECUTE 操作[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[使用 BizTalk server 執行 SQLEXECUTE 操作](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-biztalk-server.md)。  
  
-   執行 SQLEXECUTE 作業使用 WCF 服務模型時，請參閱[使用 WCF 服務模型執行 SQLEXECUTE 操作](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md)。  
  
-   執行 SQLEXECUTE 作業所使用 WCF 通道模型，請參閱[使用 WCF 通道模型執行 SQLEXECUTE 操作](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md)。  
  
-   訊息結構和執行 SQLEXECUTE 作業的 SOAP 動作，請參閱[SQLEXECUTE 操作的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)