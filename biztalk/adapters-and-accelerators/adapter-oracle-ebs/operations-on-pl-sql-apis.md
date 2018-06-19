---
title: PL-SQL Api 上的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d47b894d-1047-48ed-8f8c-865c343a12db
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5462bc4b4d6ee6a55e0e14d3ca9fccabc4dc2daf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216006"
---
# <a name="operations-on-plsql-apis"></a>PL/SQL 應用程式開發介面作業
Oracle E-business Suite 提供一組的 PL/SQL 封裝函式和預存程序的形式的 Api。 這些封裝函式，並且顯示程序中的作業為[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]。 

## <a name="plsql-apis-are-grouped-by-schema-names"></a>依結構描述名稱分組的 PL/SQL 應用程式開發介面 
PL/SQL 應用程式開發介面會依照下的結構描述名稱**成品為基礎的檢視**和**結構描述為基礎的檢視**節點，當您連接到 Oracle E-business Suite 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. 如需有關瀏覽中的 PL/SQL Api 資訊[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[瀏覽、 搜尋和 Oracle E-business 作業取得中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)。  
  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會顯示與 Oracle 資料庫，以及在 Oracle E-business Suite 中的應用程式相關聯的 PL/SQL Api**成品為基礎的檢視**和**結構描述為基礎的檢視**節點。  
  
## <a name="important-info"></a>重要資訊
  -   您可以執行 PL/SQL 應用程式開發介面與 Oracle E-business Suite 中的應用程式相關聯的作業之前，您必須設定應用程式內容。 這是因為設定應用程式內容設定 （例如責任、 組織及語言設定） 的使用者喜好設定以及成品的存取控制有助於安全 Oracle E-business Suite 中的交易。 不過，它是選擇性設定適用於 Oracle 資料庫與相關聯的 PL/SQL Api 的應用程式內容。 請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  

-   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]無法確定不論是否在使用 oracle 的 PL/SQL 應用程式開發介面中之參數指派預設值。  此外，配接器也無法確定是否要將參數定義為強制性或選擇性在 Oracle 的 PL/SQL 應用程式開發介面中。 配接器會將每個參數視為選擇性參數，而且如果未指定值參數的：  

    -   有了 default 值中指定的 Oracle，則會使用預設值。  
    -   被定義為必要參數，在 Oracle 中的例外狀況就會擲回。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)