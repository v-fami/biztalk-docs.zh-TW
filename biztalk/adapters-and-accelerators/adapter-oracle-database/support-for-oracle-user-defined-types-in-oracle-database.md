---
title: "Oracle 資料庫中的 Oracle 使用者定義型別支援 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68edf0f2-a798-4096-86ca-85d2cfa9088a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8c4f29ce8b11f74db5ff7a145449f7f212f6f6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="support-for-oracle-user-defined-types-in-oracle-database"></a>Oracle 資料庫中的 Oracle 使用者定義型別支援
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]支援 Oracle 資料庫中執行作業的成品包含 Oracle User-Defined 型別 (Udt)。 Udt 中可以存在的下列成品：  
  
-   資料表和檢視表包含 UDT 資料行。  
  
-   封裝、 預存程序和包含 UDT 參數的函式。  
  
## <a name="what-is-an-oracle-udt"></a>Oracle UDT 是什麼？  
 Oracle Udt 協助代表複雜的實體為可以在應用程式之間共用的 [單一] 物件。 比方說，是模型實際實體，例如 「 客戶 」 或 「 銷售訂單 」 可以為 Oracle 資料庫中的物件。 Oracle Udt 定義在 Oracle 資料庫中，而且它們的下列兩種類型：  
  
-   物件類型。 例如，Oracle 物件。  
  
-   集合型別。 例如，巢狀的資料表類型或 VARRAY。  
  
 Oracle UDT 的名稱會區分大小寫，而且必須以下列方式指定: [SCHEMA_NAME]。[UDT_NAME]。  
  
## <a name="how-does-the-adapter-support-oracle-udt"></a>配接器如何支援 Oracle UDT？  
 ODP.NET 支援使用 Udt 來表示 Oracle Udt 在 Oracle 資料庫中定義為.NET 型別 （自訂型別）。 自訂型別.NET 成員中定義的 Oracle UDT 屬性或項目之間的對應。 自訂型別可以是.NET 類別或結構，並可以表示 Oracle 物件或 Oracle 集合。  是否因事實，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用 ODP.NET 連接到 Oracle 資料庫時，它所繼承 Oracle Udt 的支援。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用 ODP.NET 指定自訂型別對應至.NET 自訂型別對應至資料庫中的 Oracle UDT。 若要指定自訂類型對應，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用自訂型別的處理站。 因此，若要使用 Oracle UDT，組件 （.dll 檔案） 所定義的自訂型別的處理站。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓您產生組件之自訂型別的處理站產生的中繼資料包含 Oracle UDT 成品/作業時。  
  
> [!NOTE]
>  配接器會產生用來支援 Oracle Udt ODP.NET 類別為基礎的 Oracle Udt 的組件。 如需 ODP.NET 中如何支援 Oracle Udt 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=140697](http://go.microsoft.com/fwlink/?LinkId=140697)。  
  
 若要產生設計階段使用 Oracle Udt 的組件檔案，然後稍後在執行階段中，使用它[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會公開下列繫結屬性：  
  
-   **GeneratedUserTypesAssemblyFilePath** （設計階段）  
  
-   **GeneratedUserTypesAssemblyKeyFilePath** （設計階段）  
  
-   **UserAssembliesLoadPath** （執行階段）  
  
 這些繫結屬性的相關資訊，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
## <a name="performing-operations-on-artifacts-containing-oracle-udts"></a>成品包含 Oracle Udt 上執行的作業  
 包含使用 Udt 的成品上執行作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須執行下列動作，在設計階段和執行階段。  
  
### <a name="design-time"></a>設計階段  
 您必須執行下列步驟產生結構描述時，Visual Studio 中的作業。  
  
1.  連接到 Oracle 資料庫使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]、 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 這樣的相關資訊，請參閱[連接到 Oracle 資料庫，在 Visual Studio 中使用 取用配接器服務](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md)。  
  
2.  在連接時，在**繫結屬性** 索引標籤**設定配接器**對話方塊方塊中，指定適當的值**GeneratedUserTypesAssemblyFilePath**和**GeneratedUserTypesAssemblyKeyFilePath**繫結屬性。 這些繫結屬性的相關資訊，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
3.  當您連接到 Oracle 資料庫在 Visual Studio 中時，瀏覽至包含 Oracle UDT 的必要成品。 瀏覽成品的相關資訊，請參閱[瀏覽、 搜尋和 Oracle 資料庫作業，取得中繼資料](../../adapters-and-accelerators/adapter-oracle-database/browse-search-and-get-metadata-for-oracle-database-operations.md)。  
  
4.  選取必要的成品，然後按一下**確定**。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] Oracle udt 中選取的成品會產生組件 （.dll 檔案） 以及選取之作業的中繼資料。 您在中指定的位置建立組件**GeneratedUserTypesAssemblyFilePath**繫結屬性。  
  
5.  繼續進行其餘步驟，來建置並部署您的專案。  
  
### <a name="run-time"></a>執行階段  
 您必須在 Oracle Udt 上執行作業的配接器用戶端中執行這些步驟。  
  
 **在 BizTalk Server**  
  
-   手動加入在步驟 4 建立在 「 設計階段 」 到全域組件快取 (GAC) 中您的電腦上的 Oracle UDT 組件。 或者，您可以手動複製 Oracle UDT 組件，BizTalk Server 安裝位置下。 如[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]，這通常是\<安裝磁碟機 >: \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]。  
  
-   設定時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Wcf-custom 或 Wcf-oracledb 連接埠，在**繫結**索引標籤上，指定 Oracle UDT 組件位置的**UserAssembliesLoadPath**繫結屬性。 這個繫結屬性的相關資訊，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
 **在 Visual Studio 中**  
  
-   手動加入在步驟 4 建立在 「 設計階段 」 到全域組件快取 (GAC) 中您的電腦上的 Oracle UDT 組件。 或者，您可以手動將 Oracle UDT 組件複製到專案可執行檔，通常是專案的 \bin\Debug 資料夾下的相同位置中。  
  
-   指定的 Oracle UDT 組件位置**UserAssembliesLoadPath**繫結屬性。 這個繫結屬性的相關資訊，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)