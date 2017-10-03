---
title: "如何部署 BAM 定義 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, definitions [BAM]
- managing [BAM definitions], deploying definitions
- definitions [BAM], deploying
- Deploy-All command [BAM]
ms.assetid: 02b8888c-6f6c-45dd-8445-6e507a02f5f0
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63c3572658e78c7e32722adf38436133ee098e00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-deploy-bam-definitions"></a>如何部署 BAM 定義
系統管理員使用**deploy-all-definitionfile**從活頁簿匯出 BAM 管理公用程式命令，以部署 BAM 定義從 Excel 活頁簿或 XML 定義檔。 當您執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 完整安裝時，組態精靈會自動設定 BAM 組態 XML。  
  
> [!NOTE]
>  若有多個使用者使用 Excel 的 BAM 增益集，則建議使用相同版本的 Microsoft Data Access Components (MDAC)。 否則可能會有相容性的問題。 特別是，如果您在安裝 MDAC 較新版本的電腦上建立範本，然後嘗試在安裝舊版 MDAC 的電腦上開啟該範本，就會發生編譯器錯誤。  
  
> [!NOTE]
>  每個資料維度 (例如「位置」) 只能使用一個資料項目 (例如「縣/市」)。 其他的資料維度 (例如「地區」) 便不能再使用「縣/市」。  
  
> [!IMPORTANT]
>  建議您在部署 BAM Excel 活頁簿 (.xls) 前先確認其安全性。 請使用管理電腦上的 Excel 確認 BAM Excel 活頁簿的安全性。 在部署活頁簿之前，請先開啟活頁簿，確定巨集安全性設定為「高」，而且沒有出現任何警告。  
  
> [!IMPORTANT]
>  在 BAM 資料庫中，"BAM_\<...>"命名慣例保留供所有 SQL 實體 (資料表、 索引、 預存程序、 角色等等。..)。*不這麼做*使用此命名慣例來建立任何 SQL 實體; 這樣的使用方式可能會導致未定義的行為。  
  
 在部署 BAM 定義 XML 檔之前，您必須確定用於建立該檔案的地區設定與部署所用之電腦的地區設定一致。 例如，如果您在執行 Microsoft Windows 日文版的電腦上建立檔案，則部署檔案的電腦地區設定也必須設為日文。 如果檔案和電腦的設定不一致，請將您用來執行 BAM 管理公用程式的電腦切換到正確的地區設定，並在執行公用程式之前重新啟動電腦。  
  
> [!NOTE]
>  除非所有的語言都使用相同的字碼頁，或只使用兩種語言且其中之一為英文，否則 BAM 定義 XML 檔不可包含多種語言的文字。  
  
 如需有關變更電腦地區設定的詳細資訊，請參閱作業系統的「說明」。  
  
### <a name="to-deploy-a-bam-definition"></a>部署 BAM 定義  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2.  瀏覽至追蹤資料夾，輸入**C:\Program Files\Microsoft BizTalk Server\<版本 > \Tracking**在命令提示字元。 按 ENTER 鍵。  
  
3.  型別**bm deploy-all-definitionfile-DefinitionFile:\<BAM 定義檔案 >**。  
  
4.  按 ENTER 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)   
 [BAM 安全性建議](../core/bam-security-recommendations.md)