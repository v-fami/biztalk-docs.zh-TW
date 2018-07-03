---
title: PL-SQL Api 作業 |Microsoft Docs
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
ms.openlocfilehash: 5719d74517331b30de986424bc14e7d01d128cf3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999343"
---
# <a name="operations-on-plsql-apis"></a>PL/SQL Api 的作業
Oracle E-business Suite 會提供一組的 PL/SQL Api 中的封裝函式和預存程序的形式。 這些封裝函式，並顯示程序中的作業為[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]。 

## <a name="plsql-apis-are-grouped-by-schema-names"></a>PL/SQL Api 被依據結構描述名稱 
PL/SQL Api 按下的結構描述名稱分組**成品的檢視形式**並**結構描述為基礎的檢視**節點，當您連接到 Oracle E-business Suite 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. 如需瀏覽中的 PL/SQL Api [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 瀏覽、 搜尋及取得 Oracle E-business 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)。  
  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會顯示與 Oracle 資料庫，以及在 Oracle E-business Suite 中的應用程式相關聯的 PL/SQL Api**成品的檢視形式**並**結構描述為基礎的檢視**節點。  
  
## <a name="important-info"></a>重要資訊
  -   您可以執行 Oracle E-business Suite 中的應用程式相關聯的 PL/SQL api 的作業之前，您必須設定應用程式內容。 這是因為設定應用程式內容設定 （例如責任、 組織及語言設定） 的使用者喜好設定和成品的存取控制有助於安全 Oracle E-business Suite 中的交易。 不過，它是選擇性的以設定適用於 Oracle 資料庫與相關聯的 PL/SQL Api 的應用程式內容。 請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  

- [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]無法確定是否在 Oracle 的 PL/SQL API 中的參數指派預設值。  此外，配接器也無法確定是否為強制或選擇性在 Oracle 的 PL/SQL API 中定義的參數。 配接器會將每個參數視為選擇性參數，而且如果未不指定任何值，參數的：  

  -   具有預設值中指定的 Oracle，則會使用預設值。  
  -   定義為必要參數在 Oracle 中的例外狀況會擲回。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)