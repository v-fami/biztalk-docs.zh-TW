---
title: SSO 分支機構應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSO, designing applications
- applications [SSO], application types
- SSO, application types
- SSO, application properties
- applications [SSO], properties
- applications [SSO]
- SSO, applications
- applications [SSO], designing
ms.assetid: 002ecf7e-4d52-425a-9498-0e7bd6545047
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3f276b85c05344692bc527ca5d208400bf54d10
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973991"
---
# <a name="sso-affiliate-applications"></a>SSO 分支機構應用程式
「企業單一登入」(SSO) 分支機構應用程式是代表系統或子系統 (如主控件、後端系統或您使用 SSO 連接的商務應用程式產品線) 的邏輯實體。 分支機構應用程式代表後端系統，如大型主機或 UNIX 電腦。 它也可以代表應用程式 (如 SAP)，或系統的子部分 (如 Benefits 或 Pay stub 子系統)。  
  
 當 SSO 系統管理員或 SSO 分支機構系統管理員定義分支機構應用程式時，系統管理員也必須決定誰來管理分支機構應用程式 (即應用程式系統管理員)、哪些人會成為分支機構應用程式的使用者 (即應用程式使用者)，以及 SSO 系統將使用哪些參數來驗證此分支機構應用程式的使用者 (即使用者識別碼、密碼、PIN 號碼等)。 如需有關應用程式系統管理員和應用程式使用者的詳細資訊，請參閱[SSO 使用者群組](../core/sso-user-groups.md)。  
  
## <a name="affiliate-application-types"></a>分支機構應用程式類型  
 企業 SSO 定義數個不同的應用程式類型。 不同的應用程式類型支援 Windows 帳戶和非 Windows 系統帳戶之間不同的對應類型。  
  
 應用程式類型為：  
  
 **個別**個別應用程式支援的 Windows 帳戶與非 Windows 帳戶之間的一對一對應。 在 [個別] 類型應用程式中，一個 Windows 帳戶對應到一個 (僅一個) 非 Windows 帳戶。 此對應可用於任一方向，從 Windows 到非 Windows、從非 Windows 到 Windows 或兩者，根據為此應用程式所設定的旗標而定。 因此，[個別] 應用程式可用於 Windows 初始化的 SSO、主控件初始化的 SSO 或兩者。  
  
 **群組**群組應用程式都支援一個 Windows 群組與單一非 Windows 帳戶之間的對應。 「應用程式使用者」帳戶用來定義將用於此 [群組] 應用程式的 Windows 群組。 [群組] 應用程式僅能定義一個對應，且該對應必須位於 Windows 群組與將由該 Windows 群組的所有成員用來存取非 Windows 系統的單一非 Windows 帳戶之間。 [群組] 應用程式只能用於 Windows 初始化的 SSO。  
  
 **主機群組**主機群組應用程式是在概念上的反向 [群組] 應用程式。 它們支援非 Windows 帳戶的已定義群組與單一 Windows 帳戶之間的對應。 將由非 Windows 帳戶使用的單一 Windows 帳戶，是由此應用程式的「應用程式使用者」帳戶所定義。 被允許存取此應用程式的非 Windows 帳戶群組，是透過為每個非 Windows 帳戶建立對應的方式來定義。 [主控件群組] 應用程式可能只用於主控件初始化的 SSO。  
  
## <a name="designing-an-affiliate-application"></a>設計分支機構應用程式  
 建立分支機構應用程式前，SSO 分支機構系統管理員或 SSO 系統管理員必須決定以下事項：  
  
1. **此分支機構應用程式代表什麼？** 您需要知道分支機構應用程式在 SSO 系統中將代表的非 Windows 應用程式。 例如，  
  
    應用程式名稱：APP1  
  
    描述：Pay stub 部門的應用程式  
  
    連絡人： administrator@companyname.com  
  
2. **將管理此分支機構應用程式的人員** 您需要決定此分支機構應用程式的系統管理員。 這些系統管理員組成此分支機構應用程式的 Windows 系統管理員群組。 例如，Domain\APP1AdminGroup  
  
3. **誰會使用此分支機構應用程式？** 您需要決定誰是此分支機構應用程式的一般使用者。 這些使用者代表此分支機構應用程式的 Windows 使用者群組，例如，Domain\DomainUsers。 在 Pay stub 應用程式的範例中，您可能想讓所有的使用者存取他們的 pay stub 資訊，所以您可以將網域使用者群組指定為此應用程式的使用者群組。  
  
4. **認證會分支機構應用程式使用，以驗證其使用者？** 不同的應用程式使用不同的認證來驗證使用者。 例如，有些應用程式可能會使用使用者識別碼、密碼、PIN 或是這些的組合。 您也必須決定系統是否需要在使用者提供這些認證時加上遮罩。  
  
5. **將此分支機構應用程式使用個別對應或群組對應？** 每個 Windows 使用者在後端系統都有帳戶？或是後端系統有一個帳戶供所有 Windows 使用者使用？ 在 Pay stub 應用程式的範例中，每個使用者都有自己的帳戶可以存取他們的 Pay stub 資訊，所以您需要使用個別對應。  
  
   建立分支機構應用程式後，無法修改以下屬性：  
  
-   分支機構應用程式的名稱  
  
-   與分支機構應用程式關聯的欄位  
  
-   分支機構應用程式類型 (主控件群組、個別或組態存放區)  
  
-   與分支機構系統管理員群組相同的管理帳戶。 (若選取此屬性，則分支機構系統管理員群組會做為此分支機構應用程式的應用程式系統管理員帳戶。)  
  
## <a name="affiliate-application-properties"></a>分支機構應用程式屬性  
 下表列出需要為每個建立的分支機構應用程式定義的屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|應用程式名稱|分支機構應用程式的名稱。 建立分支機構應用程式之後不能變更此屬性|  
|描述|分支機構應用程式的簡短說明|  
|連絡人|使用者可使用的此分支機構應用程式之主要連絡資訊。 (可能為電子郵件地址。)|  
|appUserAccount|包含一般使用者的使用者帳戶之 Windows 群組，這些使用者將使用此分支機構應用程式。|  
|appAdminAccount|包含系統管理員帳戶的 Windows 群組，這些系統管理員將管理此分支機構應用程式。 **注意：** 您不需要定義此屬性，如果您將 adminAccountSame 設定為 [是]。|  
  
|應用程式旗標|描述|  
|----------------------|-----------------|  
|enableApp|此分支機構應用程式的狀態。|  
|groupApp|決定此應用程式使用群組對應 (是) 或個別對應 (否)。<br /><br /> 建立應用程式後就無法變更此屬性。|  
|configStoreApp|決定此分支機構應用程式是否為「組態存放區」類型應用程式 (是)。<br /><br /> 建立應用程式後就無法變更此屬性。|  
|hostInitiatedSSO|若為主控件初始化的 SSO 類型應用程式，則啟用此項。 預設值為否。|  
|windowsInitiatedSSO|若為 Windows 初始化的 SSO 類型應用程式，則啟用此項。 預設值為是。|  
|validatePassword|此項僅適用於主控件初始化的 SSO 應用程式。 應用程式試圖擷取認證時，它必須提供 SSO 資料庫中的密碼，讓 SSO 服務用來驗證。 預設值為是。|  
|disableCredCache|SSO 伺服器儲存快取中的認證以加速存取。 預設值為否。|  
|allowTickets|決定 SSO 系統是否使用此分支機構應用程式的票證。<br /><br /> **安全性**您必須是 SSO 系統管理員，以設定此旗標。|  
|validateTickets|決定 SSO 系統在使用者贖回票證時是否驗證票證。<br /><br /> **安全性**您必須是 SSO 系統管理員，以設定此旗標。|  
|appTicketTimeOut|指定分支機構應用程式特定的票證逾時。 這項只能在更新分支機構應用程式時設定，而不是在建立分支機構應用程式時。<br /><br /> 若此應用程式已啟用票證而沒有啟用這個屬性，則會使用在 SSO 系統 (全域) 層級指定的逾時。<br /><br /> **安全性**您必須是 SSO 系統管理員，以設定此旗標。|  
|timeoutTickets|決定票證是否有到期時間。 預設值為是。<br /><br /> **安全性**除非必要，否則請勿停用票證逾時 （否）。<br /><br /> **安全性**您必須是 SSO 系統管理員，以設定此旗標。|  
|allowLocalAccounts|決定 SSO 系統中是否允許使用本機群組和帳戶。 若只有單一電腦，此旗標只能設定為 [是]。|  
|adminAccountSame|決定是否將 SSO 分支機構系統管理員群組做為應用程式系統管理員群組。<br /><br /> 建立應用程式後就無法變更此屬性。<br /><br /> **安全性**您必須是 SSO 系統管理員或 SSO 分支機構系統管理員，以設定此旗標。|  
  
|應用程式欄位|描述|描述|  
|------------------------|-----------------|-----------------|  
|欄位 [0]|\<*認證*\>： 遮罩/未遮罩|決定一般使用者必須提供才能連接分支機構應用程式的認證類型 (使用者識別碼、密碼、智慧卡)，以及此認證是否加上遮罩 (也就是說，是否在畫面上顯示使用者輸入的字元)。<br /><br /> 分支機構應用程式有多少個認證就可以輸入相同數目的欄位，但第一個欄位必須是使用者識別碼。<br /><br /> 建立應用程式後就無法變更此屬性。|  
  
## <a name="see-also"></a>另請參閱  
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)   
 [SSO 對應](../core/sso-mappings.md)   
 [管理使用者對應](../core/managing-user-mappings.md)