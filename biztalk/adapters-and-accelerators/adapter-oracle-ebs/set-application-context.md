---
title: 設定應用程式內容 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9697155-70c0-4173-80d2-d02d103c397b
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a512f2b3e198d496390bdc462af073bf05c1668
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004231"
---
# <a name="set-application-context"></a>設定應用程式內容
在  [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]，設定應用程式內容是某些 Oracle E-business Suite 成品 （介面資料表、 介面檢視、 同時執行的程式和要求集） 的必要步驟，您可以對它們執行作業之前。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不允許您執行這些成品的作業，除非您已設定應用程式內容。 不過，基礎的 Oracle 資料庫中的成品，負責使用者他們是否想要設定應用程式內容。  
  
## <a name="what-is-application-context"></a>什麼是應用程式內容  
 應用程式內容是一組可實作使用者喜好設定與成品的存取控制的 Oracle E-business Suite 中的成品相關聯的項目。 應用程式內容是由下列項目所組成：  
  
- **使用者名稱**： 使用者可以連線到 Oracle E-business Suite。  
  
- **責任**: 責任是可讓使用者存取資料和函式適用於其角色在組織中的 Oracle E-business Suite 中的存取層級。 責任可以允許存取特定應用程式，運作單位、 組的書籍，以及 windows、 函數和其他責任限制的清單。 由於指派給使用者的責任，您可以授與/限制存取的 Oracle E-business Suite 中的使用者。  
  
- **組織識別碼**: Oracle E-business Suite 支援註冊多個組織的設定。 值，組織識別碼 Org_ID 資料表資料行中儲存這些組織的相關資訊的 Oracle E-business Suite 中唯一識別這些不同的組織。 由於指派給組織有責任或明確地選取組織，您可以授與/限制存取使用者的組織。  
  
  如需有關責任的詳細資訊，請多個組織和組織識別碼，在 Oracle E-business Suite 中，搜尋[Oracle 說明中心](http://docs.oracle.com)。  
  
## <a name="setting-application-context"></a>設定應用程式內容  
 為[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]for Oracle E-business Suite 成品未建立或初始化配接器中，會連接到 Oracle E-business Suite，應用程式內容中的基礎資料庫。 您可以初始化，或設定在這些成品的應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用下列其中一項：  
  
- **繫結屬性**:[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會公開下列繫結屬性來設定應用程式內容： **OracleEBSOrganizationId**， **OracleUserName**， **OraclePassword**， **OracleEBSResponsibilityKey**， **OracleEBSResponsibilityName**，和**ApplicationShortName**。 您不需要指定所有這些繫結屬性，來設定各種成品的應用程式內容的值。 設定應用程式內容，成品所需的繫結屬性的相關資訊，請參閱[設定應用程式內容的各種成品的繫結屬性](#Binding)本主題稍後的。  
  
- **訊息內容屬性**:[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會顯示下列訊息內容屬性，來設定應用程式內容： **ApplicationShortName**， **OrganizationID****ResponsibilityKey**，並**ResponsibilityName**。 指定的使用者名稱和密碼，您必須使用的繫結屬性。 如需如何設定應用程式使用訊息內容屬性的內容資訊，請參閱[設定應用程式內容使用訊息內容屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-application-context-using-message-context-properties-in-oracle-ebs.md)。  
  
> [!IMPORTANT]
>  指定的值**OracleEBSResponsibilityKey**屬性繫結會覆寫的值**OracleEBSResponsibilityName**繫結屬性。 同樣地，將指定的值**ResponsibilityKey**訊息內容屬性會覆寫的指定值**ResponsibilityName**訊息內容屬性。  
  
### <a name="precedence-order-binding-properties-vs-message-context-properties"></a>優先順序 （繫結屬性與訊息內容屬性）  
 如果您設定應用程式內容使用繫結屬性和訊息內容屬性，指定訊息內容屬性的值會優先，並覆寫指定的繫結屬性的值。 但是，比方說，如果您的應用程式的簡短名稱指定為訊息內容屬性與其他繫結屬性時，只有應用程式的簡短名稱的值來自訊息內容屬性，而其餘部分會挑選從相關的繫結屬性。  
  
 **應用程式簡短名稱的優先順序**  
  
 在設定應用程式內容，應用程式的簡短名稱會在下列優先順序 （最高到最低）：  
  
- 中指定的應用程式簡短名稱**ApplicationShortName**訊息內容屬性。  
  
- SOAP 動作 （適用於介面資料表、 介面檢視、 同時執行的程式和只要求集） 中指定的應用程式簡短名稱。  
  
- 中指定的應用程式簡短名稱**ApplicationShortName**繫結屬性。  
  
  不過，介面資料表、 介面檢視、 同時執行的程式，和要求集，此優先順序才適用設定的應用程式內容時。 若要識別介面資料表、 介面檢視，同時執行的程式，並要求設定，在使用中的 SOAP 動作的簡短名稱的應用程式。  
  
  **優先順序的責任金鑰和責任名稱**  
  
  時設定應用程式內容，會依照下列優先順序 （最高到最低） 中會使用責任名稱與責任金鑰：  
  
- 中指定的責任金鑰**ResponsibilityKey**訊息內容屬性。  
  
- 中指定的責任名稱**ResponsibilityName**訊息內容屬性。  
  
- 中指定的責任金鑰**OracleEBSResponsibilityKey**繫結屬性。  
  
- 中指定的責任名稱**OracleEBSResponsibilityName**繫結屬性。  
  
> [!TIP]
>  **為何要使用訊息內容屬性，透過繫結來設定應用程式內容的屬性？** 如果您設定應用程式內容繫結屬性，Wcf-custom 傳送埠 for Oracle E-business 配接器可以用僅適用於特定的組織識別碼、 責任和您指定的繫結屬性的應用程式。 相反地，如果您使用訊息內容屬性可以設定 「 一般 」 的 Wcf-custom 傳送埠和訊息層級所設定的應用程式內容。  
  
### <a name="setting-application-context-for-interface-tables-interface-views-concurrent-programs-and-request-sets-mandatory"></a>介面資料表、 介面檢視、 同時執行的程式，和要求集 （必要項） 設定應用程式內容  
 您必須設定應用程式內容，再執行作業，在介面資料表、 介面檢視、 同時執行的程式，並要求集中[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 若要這樣做，您必須提供適當的值繫結屬性，或如稍早指定的訊息內容屬性。  
  
> [!IMPORTANT]
>  您無法執行作業，在介面資料表、 介面檢視、 同時執行的程式，並要求設定除非您已設定適當的值，必要的繫結屬性或訊息內容屬性。  
  
### <a name="setting-application-context-for-plsql-apis-procedures-functions-tables-and-views"></a>設定應用程式內容的 PL/SQL Api、 程序、 函數、 資料表和檢視  
  
- **PL/SQL Api**:[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開 （expose) 與 Oracle 資料庫，以及 Oracle E-business Suite 應用程式相關聯的 PL/SQL Api。 雖然是選擇性的以設定 Oracle 資料庫與相關聯的 PL/SQL api 的應用程式內容，就一定要設定 Oracle E-business Suite 應用程式相關聯的 PL/SQL api 的應用程式內容。  
  
- **程序和函數**： 它並不一定要設定應用程式內容，若要執行的 Oracle 資料庫中的程序和函式上的作業。  
  
- **資料表和檢視表**： 它並不一定要設定應用程式內容，若要執行的 Oracle 資料庫中的資料表和檢視上的作業。 不過，自訂 Oracle E-business Suite 應用程式，使用者可能會或可能無法登錄為介面資料表的基底資料庫資料表。 如果資料庫資料表不會註冊為介面資料表中，它將會顯示中的資料庫資料表以及[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 因為這些資料表與 Oracle E-business 應用程式相關聯，這些資料表上的任何作業您必須設定應用程式內容。  
  
  若要設定這些成品的應用程式內容，您必須提供適當的值繫結屬性，或如稍早指定的訊息內容屬性。  
  
### <a name="setting-application-context-for-poll-executenonquery-executereader-executescalar-and-composite-operations"></a>設定輪詢、 ExecuteNonQuery、 ExecuteReader、 ExecuteScalar 和複合作業的應用程式內容  
 除了這些成品中，您也可以設定這些成品執行的各種作業的應用程式內容。  
  
-   若要設定輪詢作業的應用程式內容，您只能使用繫結屬性所指定稍早。 設定應用程式內容，您必須提供適當的值適用於輪詢作業執行所在之成品的繫結屬性。 比方說，如果在介面資料表上執行輪詢作業，則您必須指定介面資料表的繫結屬性的值。  
  
-   若要設定的 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的應用程式內容，您必須提供適當的值繫結屬性或訊息內容屬性，如稍早指定。 設定應用程式內容，這些作業，您必須提供適當的值繫結屬性或訊息內容屬性可套用成品的作業會在其上執行。  
  
-   若要設定複合作業的應用程式內容，您必須提供適當的值繫結屬性，或如稍早指定的訊息內容屬性。 設定複合作業的應用程式內容，您必須提供適當的值繫結屬性或訊息內容屬性都適用於個別的作業。 例如，如果複合作業包含兩項作業： 一個在介面資料表和資料庫上的其他資料表，然後您必須指定的繫結屬性或介面資料表，以及繫結的訊息內容屬性的值資料庫資料表的訊息內容屬性或屬性。  
  
    > [!IMPORTANT]
    >  所有這些作業，就一定要設定應用程式內容，如果 Oracle E-business Suite （介面資料表、 介面檢視、 同時執行的程式或要求集） 中的成品執行作業。 如果基礎資料庫中的成品執行作業，則它不一定要設定應用程式內容。 比方說，如果您正在執行輪詢資料表上的作業介面，它是必要的設定應用程式內容，而如果輪詢作業在資料表上執行，它並不一定要設定應用程式內容。  
  
## <a name="setting-the-language-for-performing-operations"></a>設定執行作業的語言  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援 Oracle E-business Suite、 多國語言支援 (MLS) 功能，並可讓您在執行作業時指定的語言。 配接器會公開**語言**下方的內容繫結**MlsSettings**繫結屬性和**語言**訊息內容屬性設為指定的語言執行作業。  
  
 指定的值**語言**訊息內容屬性會覆寫的值**語言**下的屬性繫結**MlsSettings**繫結屬性。 如需詳細資訊**MlsSettings**繫結屬性，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
##  <a name="Binding"></a> 設定各種成品的應用程式內容繫結屬性  
 下表提供您必須指定適當的值來設定各種成品的應用程式內容的繫結屬性的相關資訊：  
  
|成品|OracleEBSOrganizationId|OracleUserName|OraclePassword|OracleEBSResponsibilityKey<br />中的多個<br />OracleEBSResponsibilityName|ApplicationShortName|  
|---|---|---|---|---|---|  
|介面資料表和介面檢視|√*|√|√|√||  
|同時執行的程式|√*|√|√|√||  
|要求集|√*|√|√|√||  
|PL/SQL Api|√*|√|√|√|√|  
|程序及函數|√*|√|√|√|√|  
|資料表和檢視表|√*|√|√|√|√|  
  
 **√\* = True**  
  
> [!IMPORTANT]
> - 預設值**OracleEBSOrganizationId**繫結屬性 （選擇性） 為 null。 如果您指定的值**OracleEBSOrganizationId**屬性，繫結[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]設定應用程式內容時，此值設定工作階段的 ORG_ID。  
>   -   指定的值**OracleEBSResponsibilityKey**屬性繫結會覆寫的指定值**OracleEBSResponsibilityName**繫結屬性。  
  
 如需每個繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)