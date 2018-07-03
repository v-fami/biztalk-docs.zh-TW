---
title: Oracle 資料庫中的 SQLEXECUTE 作業 |Microsoft Docs
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
ms.openlocfilehash: cfae55d12ce3b244001bf04aef48ff40b97d97a1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000509"
---
# <a name="sqlexecute-operation-in-oracle-database"></a>Oracle 資料庫中的 SQLEXECUTE 作業
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現一組標準的 Oracle 資料庫成品的作業。 藉由使用這些作業，您可以執行如下呼叫的動作，Oracle 函式或程序，或執行基本 SQL 資料操作語言 (DML) 作業在資料表上。 不過，有可能是由您的商務邏輯驅動的案例會要求您執行作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不會不會出現。 例如，您可能想要：  
  
- 對資料庫成品是不會顯示所執行作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; 例如，取得 CURVAL 或 NEXTVAL 的 Oracle 序列。  
  
- 執行資料定義語言作業;例如，建立資料表。  
  
- 在設計階段; 沒有為資料庫成品上執行作業比方說，更新您的商務邏輯所建立的暫存資料表中的記錄。  
  
- 執行資料表上更複雜的 DML 作業，作業的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]呈現; 比方說，若要執行的查詢包含聯結子句。  
  
  這種情況下，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]呈現 SQLEXECUTE 作業。 SQLEXECUTE 作業時，會顯示在根節點 （/） 上，在**選取一個類別** 窗格中的[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。  
  
  藉由使用 SQLEXECUTE 作業，您可以執行的 Oracle 資料庫上的參數化的 SQL 陳述式。 SQLEXECUTE 作業支援參數集可讓您執行一次的每一組相同的 SQL 陳述式所組成的輸入的參數區塊。 SQLEXECUTE 作業會傳回一組標準的記錄中的 SQL 陳述式的結果。  
  
> [!NOTE]
>  您可以傳遞中及在 OUT 參數，程序、 函數和 SQLEXECUTE 作業中的封裝。 叫用的成品將會執行以提供的 Oracle 資料庫中; 上的參數不過，在 SQLEXECUTE 作業不會傳回外的值和在 OUT 參數，用戶端。 如果您想要叫用程序、 函式或套件，我們建議您這麼做叫用專用的作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開 （expose) 這些 Oracle 成品。  
  
 如需詳細資訊：  
  
- 使用執行 SQLEXECUTE 作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 使用 BizTalk server 執行 SQLEXECUTE 作業](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-biztalk-server.md)。  
  
- 執行 SQLEXECUTE 作業使用 WCF 服務模型，請參閱[使用 WCF 服務模型執行 SQLEXECUTE 作業](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md)。  
  
- 執行 SQLEXECUTE 作業所使用 WCF 通道模型，請參閱[使用 WCF 通道模型執行 SQLEXECUTE 作業](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md)。  
  
- 訊息結構和執行 SQLEXECUTE 作業的 SOAP 動作，請參閱[LEXECUTE 作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)