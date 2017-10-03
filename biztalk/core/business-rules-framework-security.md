---
title: "商務規則架構安全性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, code samples
- security, business rules
- artifacts, security
- security, artifacts
- business rules, security
ms.assetid: 86582d3a-259e-47f2-9f72-8dbbe0051503
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2c3a38190d242c85b134a791a8c2cd05c208050
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="business-rules-framework-security"></a>商務規則架構安全性
「商務規則引擎」在主控件應用程式的安全性內容中作業。 規則引擎執行個體執行期間的識別則是確認的執行緒內容會叫用**Policy.Execute**方法。  
  
## <a name="default-security-configuration"></a>預設安全性組態  
 當您安裝 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]、 兩個 Microsoft Windows 群組建立依預設，一個給系統管理員，一個給使用者: 「 BizTalk Server 系統管理員 」 和 「 BizTalk 應用程式使用者 」。 這兩個 Windows 群組分別為 BTS_ADMIN_USERS 和 BTS_HOST_USERS SQL Roles 的成員，而 BTS_ADMIN_USERS 和 BTS_HOST_USERS SQL Roles 分別為 RE_ADMIN_USERS 和 RE_HOST_USERS SQL Roles 的成員。  
  
 當規則存放區建立時即建立了預設 SQL 角色：BTS_ADMIN_USERS、BTS_HOST_USERS、RE_ADMIN_USERS 和 RE_HOST_USERS。  
  
|預設 Windows 群組|SQL 角色|  
|----------------------------|---------------|  
|BizTalk Server 系統管理員|RE_ADMIN_USERS|  
|BizTalk 應用程式使用者|RE_HOST_USERS|  
  
 只有 RE_ADMIN_USERS 角色中的使用者可以執行更新部署和實體存取保護組態資料表的預存程序。 這表示部署、解除部署和保護組態全部都只能由規則引擎管理員執行。 RE_HOST_USERS 角色中的使用者可以執行 SQL 角色存放區中的其他預存程序。  
  
 無論安裝規則引擎的順序為何，若「規則引擎更新服務」帳戶尚未具有資料庫存取權，規則引擎組態程序會將 RE_HOST_USERS SQL 角色的成員資格授與此帳戶。 但是，若規則引擎在初始 BizTalk 安裝 BizTalk 之後才安裝，則因為主控件建立已經完成，所以主控件特定的使用者群組將不會新增到「規則引擎」資料庫中的 BTS_HOST_USERS SQL 角色。 您必須手動執行此步驟。  
  
## <a name="artifact-level-security"></a>成品層次安全性  
 除了預設安全性組態之外，「商務規則引擎」也可提供成品—原則和詞彙層次的安全性。  
  
 每個原則或詞彙版本均有一或多個與其相關聯的授權群組。 「授權」群組是 Microsoft Windows 使用者、SQL 使用者、SQL 角色以及 Windows 群組的具名清單，而每個類型各具有特定的存取層次。  
  
 當新原則或詞彙在規則存放區中建立時，依照預設，只有建立它的使用者和規則引擎管理員同時具有讀取/執行和修改/刪除存取權。 規則引擎管理員可以設定哪些使用者 (在使用者認證之下執行的程序) 具有存取層次或權限以執行不同作業—讀取/執行、修改/刪除、完整權限或沒有權限。  
  
 預設不會啟用成品特定安全性。 目前不能透過使用者介面設定成品層次安全性。 不過，可以使用「商務規則引擎」系統管理員認證以程式設計的方式設定。 以下程式碼片段顯示如何建立新的授權並將群組與規則集建立關聯。  
  
```  
RuleSet rs;  
string RSName;     
  
// Create new user  
AuthorizationGroupEntry newuser = new AuthorizationGroupEntry(UserName, UID);  
AuthorizationGroupEntryCollection AGEC = new AuthorizationGroupEntryCollection();  
AGEC.Add(newuser);  
  
// Define new authorization group collection  
AuthorizationGroupCollection AGC = new AuthorizationGroupCollection();  
  
// Create new authorization group  
AuthorizationGroup AG = new AuthorizationGroup(GroupName, AccessPermit, AGEC);  
  
//add the authorization group to the authorization group collection  
AGC.Add(AG);  
  
//saving the authorization group collection to the rule store  
m_sqlRS.SaveAuthorizationGroups(AGC);  
  
rs = m_sqlRS.GetRuleSet(rsInfo[0]);                 
RSName = rs.Name;  
  
// Associate authorization group to the ruleset  
m_sqlRS.SetRuleSetAuthorizations(RSName, AGC);  
  
// Get ruleset by name from SQL rule store  
RuleSetInfoCollection rsInfo = m_sqlRS.GetRuleSets("myRuleSet", RuleStore.Filter.All);  
```  
  
> [!NOTE]
>  使用成品層次安全性可能會降低效能，因為此原則必須對每個執行進行資料庫尋查，以便在傳回規則引擎的執行個體之前評估應用程式的存取層次。  
  
## <a name="see-also"></a>另請參閱  
 [商務規則引擎的重要安全性注意事項](../core/important-security-notes-for-the-business-rule-engine.md)