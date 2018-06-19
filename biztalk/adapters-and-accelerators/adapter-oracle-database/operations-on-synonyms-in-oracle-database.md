---
title: Oracle 資料庫內的同義字上的作業 |Microsoft 文件
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
ms.openlocfilehash: 006107f5f21d017a79b7aa11f70fb1728bb5639a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214958"
---
# <a name="operations-on-synonyms-in-oracle-database"></a>Oracle 資料庫內的同義字上的作業
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓您在同義字上執行作業。 同義字是別名或資料庫物件 （例如資料表、 檢視、 預存程序、 函數和封裝） 的好記名稱。 如需在 Oracle 中的同義字的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=138058](http://go.microsoft.com/fwlink/?LinkId=138058)。  
  
## <a name="advantages-of-using-synonyms"></a>使用同義字的優點  
 同義字是在下列案例中很有幫助：  
  
-   **使用不同的結構描述**： 如果您使用不同的結構描述，且需要存取整個結構描述的物件，您必須使用不同的 SQL 陳述式來存取這些物件。 您可以在結構描述中，建立物件的同義字，並用於 SQL 陳述式中的同義資料表，以存取物件。 如果您需要存取基礎物件不同的結構描述中，修改同義字指向不同的結構描述中物件的定義。 因此，同義資料表為基礎的應用程式繼續運作，不需要修改 SQL 陳述式中。  
  
     例如，假設您的測試和實際執行環境中的兩個相同的結構描述:"Test"和"Prod"。 若要存取 「 測試 」 結構描述中稱為 「 員工 」 的資料表，您必須使用`Test.Employee`或`Employee`（如果 「 測試 」 的預設結構描述） 中 SQL 陳述式。 如果您想要在實際執行結構描述中使用 「 員工 」 資料表，您現在必須使用`Prod.Employee`或`Employee`（變更預設結構描述為"Prod"） 在您的 SQL 陳述式。 若要解決此問題，您可以建立同義字"Test.Employee 」 資料表 (例如"EMP")，並將它用於您的 SQL 陳述式。 每當您需要在 「 Prod.Employee 」 資料表上執行作業，修改為指向 「 Prod.Employee 「 資料表 」 EMP"同義字的定義。 這可確保您不需要修改您的 SQL 陳述式，以在不同的結構描述物件上執行作業。  
  
-   **基礎物件變更**： 同義字隔離您的名稱或位置執行的作業的基礎物件中的任何變更。 您可以修改同義字定義，以容納的名稱或基礎物件的位置中的任何變更。  
  
     例如，假設您使用表格中其中一個預存程序。 現在，如果變更資料表名稱或資料表移至其他位置然後預存程序將會停止運作。 若要解決這個問題，，您可以使用同義字在預存程序中，資料表，並更新同義字定義，如果沒有名稱或資料表的位置中的變更。  
  
-   **簡化及安全存取**： 在分散式環境中，您必須使用結構描述名稱，以及物件名稱，以確保您要存取正確的物件。 此外，您也必須確認使用者具有必要的目標物件上的權限。 為了簡化這種情況，可以藉由建立同義字具有完整的完整的路徑物件，指定物件的簡單名稱，然後授與同義字上的適當權限。  
  
## <a name="working-with-synonyms-in-the-adapter"></a>使用同義字在配接器  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開在 Oracle 中的同義字：  
  
-   資料表  
  
-   檢視  
  
-   預存程序  
  
-   函數  
  
-   Packages  
  
 每個成品的同義字會公開在個別的基礎成品一起[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 例如，**資料表**節點下的結構描述會顯示所有資料表，以及資料庫資料表的同義字的結構描述中**檢視**節點下的結構描述會都顯示所有的檢視表，沿著同義字在結構描述和等等的資料庫檢視。  
  
-   在資料表和檢視表上建立同義字，相同的作業會公開與基礎資料表和檢視表分別。 例如，如果基礎資料表和檢視表包含 LOB 資料行，這些資料表和檢視表的同義字會也會公開 ReadLOB 和 UpdateLOB 作業。  
  
-   建立預存程序、 函數和封裝上的同義字，同義字被公開為與個別的基礎預存程序、 函數和封裝結構描述中的作業。  
  
> [!NOTE]
>  [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援只有本機的同義字。 這表示只有那些同義字受到配接器為目標的本機伺服器上的成品。  
  
 此外，同義字的訊息動作為基礎的物件，但不包括其執行動作的成品名稱相同。 例如，訊息動作**選取**SCOTT 結構描述中的資料表上的作業正在： `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/[TABLE_NAME]/Select`。 如果您執行同義字上的選取作業的相同資料表中 SCOTT 結構描述的訊息動作便會是： `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/[SYNONYM_NAME]/Select`。  
  
 當您叫用配接器在同義字上的作業時，配接器會呼叫執行作業的 Oracle 資料庫中的同義字。 不過，配接器使用的基礎物件名稱的同義資料表定義中擷取的中繼資料。  
  
 同義字可以用於標準輸出作業、 複合作業以及輪詢。  
  
> [!NOTE]
>  您可以搜尋的同義字[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]就像其他物件。 不過，您無法搜尋同義字的封裝，將略過層級節點內的程序就可以如同在封裝內的程序一樣。 搜尋作業，在配接器的相關資訊，請參閱[瀏覽、 搜尋和 Oracle 資料庫作業，取得中繼資料](../../adapters-and-accelerators/adapter-oracle-database/browse-search-and-get-metadata-for-oracle-database-operations.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)