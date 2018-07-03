---
title: 對 Oracle 資料庫中的同義字的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 608e8c36-ac78-4d7d-aca4-be552505fc2b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e782f5257658f9145bda3cabc67a306acf22f94
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986063"
---
# <a name="operations-on-synonyms-in-oracle-database"></a>對 Oracle 資料庫中的同義字的作業
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓您在同義字上執行作業。 同義字是別名或易記名稱 （例如資料表、 檢視、 預存程序、 函數和封裝） 的資料庫物件。 如需有關在 Oracle 中的同義字的詳細資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=138058 ](http://go.microsoft.com/fwlink/?LinkId=138058)。  
  
## <a name="advantages-of-using-synonyms"></a>使用同義字的優點  
 同義字是在下列案例很有幫助：  
  
-   **使用不同的結構描述**： 如果您正在使用不同的結構描述，以及需要存取整個結構描述的物件，您必須使用不同的 SQL 陳述式來存取這些物件。 您可以在結構描述中，建立物件的同義字，並在您的 SQL 陳述式中使用同義字，來存取物件。 如果您需要存取基礎物件在不同的結構描述中，修改為指向不同的結構描述中的物件同義資料表的定義。 因此，根據同義字的應用程式會繼續運作而不需修改 SQL 陳述式中。  
  
     例如，假設您針對測試和生產環境中有兩個相同的結構描述:"Test"和"Prod"。 若要存取 「 測試 」 結構描述中名為 「 Employee 」 的資料表，您必須使用`Test.Employee`或`Employee`（如果 「 測試 」 的預設結構描述） 在您的 SQL 陳述式。 如果您想要用於實際執行結構描述中的 「 員工 」 資料表，您現在必須使用`Prod.Employee`或`Employee`（變更到 「 生產 」 的預設結構描述） 在您的 SQL 陳述式。 若要解決此問題，您可以建立同義字"Test.Employee 」 資料表 (例如"EMP")，並將它用於您的 SQL 陳述式。 每當您需要執行 「 Prod.Employee 」 資料表上的作業，修改為指向 「 Prod.Employee 「 資料表 」 EMP"同義字的定義。 這可確保您不需要修改您的 SQL 陳述式，以在不同的結構描述物件上執行作業。  
  
-   **基礎物件變更**: 同義字會隔離您從的名稱或位置執行的作業的基礎物件中的任何變更。 您可以修改的同義資料表定義，以容納的名稱或位置的基礎物件中的任何變更。  
  
     例如，假設您在其中一個您預存程序中使用資料表。 現在，如果資料表名稱變更或資料表移到其他位置然後您的預存程序將會停止運作。 若要解決這個問題中,，您可以使用預存程序中，資料表的同義資料表並更新同義字定義，如果沒有變更名稱或資料表的位置。  
  
-   **簡化且安全的存取**： 在分散式環境中，您必須使用結構描述名稱，以及物件名稱，以確保存取正確的物件。 此外，您也必須確定使用者具有必要的目標物件上的權限。 為了簡化此作業，您可以藉由建立同義字具有完整的完整的路徑物件，指定物件的簡單名稱，然後再授與同義字的適當權限。  
  
## <a name="working-with-synonyms-in-the-adapter"></a>使用配接器中的同義字  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會公開在 Oracle 中的同義字：  
  
- 資料表  
  
- 檢視  
  
- 預存程序  
  
- 函數  
  
- Packages  
  
  每個成品的同義字會公開與在個別的基礎構件[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 比方說，**表格**節點下的結構描述會顯示在結構描述的資料表及資料庫資料表的同義字**檢視**節點下的結構描述會顯示沿著檢視所有的同義字資料庫中的檢視結構描述和等等。  
  
- 在資料表和檢視表上建立的同義字，相同的作業會公開基礎的資料表和檢視分別。 比方說，如果基礎資料表和檢視表包含 LOB 資料行，這些資料表和檢視表的同義資料表也會公開 「 ReadLOB 和 UpdateLOB 」 作業。  
  
- 建立預存程序、 函數和封裝的同義字，同義字會公開為與個別的基礎預存程序、 函數和結構描述中的封裝作業。  
  
> [!NOTE]
>  [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援只有本機的同義字。 這表示，只有這些同義字支援配接器為目標的本機伺服器上的成品。  
  
 此外，同義字的訊息動作為基礎的物件，但不包括在其執行此動作的構件名稱相同。 例如，訊息動作**選取 ** SCOTT 結構描述中的資料表上的作業： `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/[TABLE_NAME]/Select`。 如果您執行同義字上的選取作業的相同資料表中 SCOTT 結構描述的訊息動作便會是： `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/[SYNONYM_NAME]/Select`。  
  
 當您叫用配接器中的同義字上的作業時，配接器會呼叫以執行作業的 Oracle 資料庫中的同義字。 不過，配接器會以中繼資料的同義資料表定義中使用 基礎物件的名稱。  
  
 同義字可用於一般的傳出作業、 複合作業，以及輪詢。  
  
> [!NOTE]
>  您可以搜尋的同義字[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]就像其他物件。 不過，您無法搜尋從略過層級節點的同義字套件內的程序，您可以在進行套件內的程序。 如需搜尋配接器中的作業資訊，請參閱[瀏覽、 搜尋及取得 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/browse-search-and-get-metadata-for-oracle-database-operations.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)