---
title: 支援 Oracle 資料庫中的 Oracle 使用者定義型別 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 68edf0f2-a798-4096-86ca-85d2cfa9088a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bf839d214d0877ea51430cd0c4a7784ebfa3cc8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007055"
---
# <a name="support-for-oracle-user-defined-types-in-oracle-database"></a>Oracle 資料庫中的 Oracle 使用者定義型別支援
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]支援 Oracle 資料庫中執行作業的成品包含 Oracle User-Defined 型別 (Udt)。 Udt 可出現在下列成品：  
  
-   資料表和檢視表包含 UDT 資料行。  
  
-   封裝、 預存程序和包含 UDT 參數的函式。  
  
## <a name="what-is-an-oracle-udt"></a>Oracle UDT 是什麼？  
 Oracle Udt 協助當作可在應用程式之間共用的 「 單一 」 物件的複雜的實體。 比方說，就能夠模型真實世界實體，例如 「 客戶 」 或 「 銷售訂單 」 做為 Oracle 資料庫中的物件。 Oracle Udt 定義在 Oracle 資料庫中，以及它們有下列兩種類型：  
  
- 物件類型。 例如，Oracle 物件。  
  
- 集合型別。 例如，巢狀的資料表類型或 VARRAY。  
  
  Oracle UDT 的名稱區分大小寫，而且必須以下列方式指定: [SCHEMA_NAME]。[UDT_NAME]。  
  
## <a name="how-does-the-adapter-support-oracle-udt"></a>配接器如何支援 Oracle UDT？  
 ODP.NET 藉由代表在 Oracle 資料庫中定義為.NET 類型 （自訂） 的 Oracle Udt 支援 Udt。 自訂型別.NET 成員中定義 Oracle UDT 屬性或項目間的對應。 自訂型別可以是.NET 類別或結構，並可以表示 Oracle 物件或 Oracle 集合。  而事實上，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用 ODP.NET 連接到 Oracle 資料庫時，它會繼承 Oracle Udt 的支援。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用 ODP.NET 指定自訂型別對應的.NET 自訂型別對應至資料庫中的 Oracle UDT。 若要指定自訂類型對應，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用的自訂型別的處理站。 因此，若要使用 Oracle UDT，則組件 （.dll 檔案） 便不需要定義的自訂型別的處理站。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓您產生的自訂型別的處理站產生包含 Oracle UDT 成品/作業的中繼資料時的組件。  
  
> [!NOTE]
>  配接器會產生用來支援 Oracle Udt ODP.NET 類別為基礎的 Oracle Udt 的組件。 如需如何支援 ODP.NET Oracle Udt 的詳細資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=140697 ](http://go.microsoft.com/fwlink/?LinkId=140697)。  
  
 產生設計階段使用 Oracle Udt 的組件檔，並接著會將該執行階段，在稍後[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會公開下列繫結屬性：  
  
- **GeneratedUserTypesAssemblyFilePath** （設計階段）  
  
- **GeneratedUserTypesAssemblyKeyFilePath** （設計階段）  
  
- **UserAssembliesLoadPath** （執行階段）  
  
  這些繫結屬性的相關資訊，請參閱[Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
## <a name="performing-operations-on-artifacts-containing-oracle-udts"></a>在包含 Oracle Udt 的構件上執行作業  
 包含使用 Udt 的構件上執行作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須執行下列動作，在設計階段和執行階段。  
  
### <a name="design-time"></a>設計階段  
 您必須執行這些步驟產生結構描述時，Visual Studio 中的作業。  
  
1. 連接到 Oracle 資料庫使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 如需這種方式的資訊，請參閱[連接到 Oracle 資料庫，在 Visual Studio 中使用 取用配接器服務](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md)。  
  
2. 在連接時，在**繫結屬性**索引標籤**設定介面卡**對話方塊方塊中，指定適當的值，如**GeneratedUserTypesAssemblyFilePath**並**GeneratedUserTypesAssemblyKeyFilePath**繫結屬性。 這些繫結屬性的相關資訊，請參閱[Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
3. 當您連接到 Oracle 資料庫，在 Visual Studio 中時，瀏覽至必要的成品，其中包含 Oracle UDT。 如需瀏覽成品的詳細資訊，請參閱[瀏覽、 搜尋及取得 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/browse-search-and-get-metadata-for-oracle-database-operations.md)。  
  
4. 選取必要的成品，然後按一下**確定**。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] Oracle udt 中選取的成品產生組件 （.dll 檔案） 以及所選作業的中繼資料。 組件中所指定的位置建立**GeneratedUserTypesAssemblyFilePath**繫結屬性。  
  
5. 繼續進行其餘步驟，用於建置及部署您的專案。  
  
### <a name="run-time"></a>執行階段  
 您必須在配接器用戶端在 Oracle Udt 上執行作業來執行這些步驟。  
  
 **在 BizTalk Server**  
  
- 手動加入在步驟 4 建立在 「 設計階段 」 至全域組件快取 (GAC) 中您的電腦上的 Oracle UDT 組件。 或者，您可以手動複製 Oracle UDT 組件在 BizTalk Server 安裝位置。 BizTalk server，這通常是\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。  
  
- 在設定時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Wcf-custom 或 Wcf-oracledb 連接埠，在**繫結**索引標籤上，指定 Oracle UDT 組件位置的**UserAssembliesLoadPath**繫結屬性。 這個繫結屬性的相關資訊，請參閱[Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
  **在 Visual Studio 中**  
  
- 手動加入在步驟 4 建立在 「 設計階段 」 至全域組件快取 (GAC) 中您的電腦上的 Oracle UDT 組件。 或者，您可以手動將 Oracle UDT 組件複製到專案可執行檔，通常是專案的 \bin\Debug 資料夾下的相同位置中。  
  
- 指定 Oracle UDT 組件的位置**UserAssembliesLoadPath**繫結屬性。 這個繫結屬性的相關資訊，請參閱[Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)