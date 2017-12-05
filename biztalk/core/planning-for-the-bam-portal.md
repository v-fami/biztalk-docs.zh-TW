---
title: "規劃 BAM 入口網站 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM portal, security
- BAM portal, prerequisites
- BAM portal, deploying
- developing, BAM portal
- planning, BAM portal
- BAM portal, planning
- BAM portal, developing
- deploying, BAM portal
- security, BAM portal
ms.assetid: 8a8bd331-c5a8-4d8b-9e93-96e6cd581a1d
caps.latest.revision: "36"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85f7291d56d662a8e3a9d46308d6b16ca2a1cafc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="planning-for-the-bam-portal"></a>規劃 BAM 入口網站
本主題說明您在規劃商務活動監控 (BAM) 入口網站部署時應該考量的事項。  
  
## <a name="prerequisites"></a>必要條件  
 **系統需求**。 除了 BizTalk Server 的系統需求，您必須安裝下列軟體才能安裝 BAM 入口網站：  
  
-   Internet Information Services (IIS)  
  
-   Microsoft Office Excel  
  
-   Microsoft Internet Explorer  
  
-   Microsoft .NET Framework  
  
-   Microsoft XML Core Services (MSXML) 6.0  
  
-   Microsoft Data Access Components (MDAC) 2.7  
  
## <a name="configuration-planning"></a>組態規劃  
 **從舊版的 BizTalk Server 移轉**。 在移轉之後從舊版的 BizTalk Server，您安裝 BAM 入口網站中的現有頁面可能不再運作。 如 BAM 入口網站中順利運作，請參閱考量和指導方針的 BAM 提供 BizTalk Server 升級指南。  
  
 **資料庫**。 規劃資料庫時，請考量下列事項：  
  
-   資料庫務必規劃索引以提升效能。 進度維度上的日期和時間資料行通常需要索引。 查詢未設置索引的進度維度不僅速度緩慢，還會對 BAM 主要匯入資料表的效能造成負面影響。  
  
-   您必須考慮是否設定 BAM 不使用警示。  
  
 **SQL Server Notification Services**。 SQL Server Notification Services 不支援以本機主機或 IP 位址取代伺服器名稱來識別伺服器。  在以下兩種情形時可能需要注意這一點：  
  
1.  組態期間 - 當您選取 BAM 並開啟警示時，組態程序會要求提供伺服器名稱。  
  
2.  修改組態 .xml 檔案 - 針對組態程序所建立的組態 .xml 檔案，您嘗試進行修改以供重複使用。  
  
 **IIS 安裝**。 BAM 入口網站只能在 32 位元模式下執行。 如果您要在 64 位元電腦上安裝 IIS，則您必須確定在 32 位元模式上已啟用 ASP.NET 2.0。 若要這樣做，請開啟 IIS 管理員中，開啟**應用程式集區**，選取應用程式集區 (BAMAppPool)，然後按**進階設定**。 在 [啟用 32 位元應用程式] 中，選取 [True]。 如需詳細資訊，請參閱 BizTalk Server 升級指南 》。  
  
## <a name="deployment-planning"></a>部署規劃  
 **多部電腦部署**。 BizTalk Server 部署是否位於多部電腦環境中？ 如果 BAM 入口網站和警示資料庫設置在不同的伺服器上，請務必提高多伺服器環境的查詢服務逾時值。 如需其他組態資訊，請參閱[自訂 BAM 入口網站組態](../core/customizing-the-bam-portal-configuration.md)。  
  
-   **多重文化特性部署**。 BizTalk Server 部署是否位於多重文化特性的環境中？ 當您安裝 BizTalk Server 時，使用者介面 (UI) 將採用所安裝版本的語言，BAM 入口網站則會沿用網站設定者的文化特性設定。 若要修改 BAM 入口網站的 web.config 檔案，以反映適當的文化特性設定，請參閱[自訂 BAM 入口網站組態](../core/customizing-the-bam-portal-configuration.md)。  
  
 **叢集部署**。 部署的環境是否為網路負載平衡 (NLB) 叢集？ 請參閱[自訂 BAM 入口網站組態](../core/customizing-the-bam-portal-configuration.md)的額外組態資訊。  
  
 **SSL**。 部署 BAM 入口網站的 IIS 安裝是否使用 SSL？ 請參閱[自訂 BAM 入口網站組態](../core/customizing-the-bam-portal-configuration.md)的額外組態資訊的主題。  
  
 建立檢視的使用者必須安裝 Excel 的 BAM 增益集。  
  
## <a name="permissions"></a>Permissions  
 **BAM 管理員**。 BAM 管理員 (bm.exe) 的 add-account 命令不會自動授與資料庫權限給新增的使用者。 這是因為執行 BAM 管理員只需要 dbo 權限。 因此，您必須隸屬於以下所述之特定 SQL Server 群組，否則若從 BAM 入口網站存取即時彙總 (RTA) 將導致 SQL Server 失敗。  
  
 **SQL Server 角色**。 若要授與使用者存取資料庫的權限，您必須是 securityadmin 或 sysadmin 群組的成員。  
  
 securityadmin 或 sysadmin 群組的成員可以經由執行 sp_grantdbaccess 和 sp_grantlogin 授與權限。  
  
 如需有關 SQL Server 角色的詳細資訊，請查看 「 角色在 SQL Server 架構 」 [http://go.microsoft.com/fwlink/?LinkId=56205](http://go.microsoft.com/fwlink/?LinkId=56205)。  
  
## <a name="development-planning"></a>開發作業規劃  
 **樞紐分析表的連接字串**。 BAM 管理員公用程式在部署期間，不一定會更改即時彙總 (RTA) 樞紐分析表定義中的連接字串。 之所以未更改，是因為 RTA 樞紐分析表既有的 OLAP 連接字串已遭手動編輯，但只是數值機碼的大小寫不正確而已。 例如，在 BAM 定義 XML 檔案中的底下這一行，機碼是 RTARef 而非原本應有的 RtaRef：  
  
 **\<樞紐分析表檢視 CubeRef ="POCube"RTARef ="POAmountByLocation"\>**  
  
 這會造成從 OLAP Cube 產生樞紐分析表，而不是從 RTA 樞紐分析表產生。  
  
 **欄位名稱**。 建議您在開發監控方案時，選擇易於區別的欄位名稱命名慣例。 對於 BAM 定義的檢視區段以及彙總的 OLAP Cube，BAM 並未限定兩者所使用的名稱必須互不相同。  在此情況下，[活動搜尋] 查詢建立器上的欄位選擇器和欄位選擇下拉式清單中，可能包含兩個同名欄位。 屆時，一旦您嘗試選取正確的欄位以包括在結果中，可能就會發生錯誤。  
  
 BizTalk Server 連接埠如果使用通過管線，便無法追蹤訊息內容中的資料。 通過管線不會將訊息類型評估為結構描述名稱，以致所有訊息的結構描述都是空值。  
  
-   由於追蹤設定檔對應至連接埠加上結構描述的組合，因此試圖追蹤通過管線的訊息內容資料將一無所獲。  
  
 **樞紐分析表的名稱**： 規劃及開發使用者體驗時彙總工作 BAM 入口網站中，您應該建立使用者易記的名稱，您在 Excel 中建立的樞紐分析表。  若要自訂名稱，請以滑鼠右鍵按一下樞紐分析表，再從快顯功能表選取 [表格選項]。  
  
 **日期範圍**。 當建立查詢和執行個體警示使用 [活動搜尋] 頁面請記住，如果 @@DateFirst SQL 查詢中的值與 CultureInfo.CurrentCulture.DateTimeFormat.FirstDayOfWeek 值不符，然後在顯示的日期範圍搜尋頁面不會符合用來產生彙總的週別界限。  
  
 例如，假設 SQL Server 一週的開始日期設定為星期日，則 2005 年第 2 週的日期範圍會從 1/2/2005 到 1/8/2005，且 SQL Server 和 OLAP 所顯示的第 2 週彙總均以此日期範圍為準。 不過，如果 BAM 入口網站指定的一週開始日期是星期六，則一旦使用者向下切入到 2005 年第 2 週，就會在搜尋頁面上看到從 1/8/2005 到 1/14/2005 的日期範圍。 因此，搜尋查詢所傳回的值可能與樞紐分析表顯示的彙總值不符。  
  
 若要得到期望的結果，請調整查詢的時間範圍以取得所需的日期範圍。  
  
 **分散式導覽**。 BAM 入口網站的分散式導覽功能，能讓使用者檢視跨越遠端界限的活動關係。 開發活動時請考量下列事項：  
  
-   同一個檢視中顯示的相關活動可能來自不同的 BAM 主要匯入資料庫。 活動可能有相同的名稱但位於不同的伺服器，譬如兩個不同部門都有「訂單」活動。 如果使用者在 BAM 入口網站中從 [我的檢視] 窗格選取檢視，就會看到兩個活動並列於每個工作下方。  
  
-   如果您有多部伺服器架設 BAM 入口網站讓使用者查看部署檢視，為了提供相同的使用經驗，每一部伺服器對其本機 BAM 主要匯入資料庫執行查詢的各項設定務求一致。  
  
## <a name="see-also"></a>請參閱  
 [自訂 BAM 入口網站設定](../core/customizing-the-bam-portal-configuration.md)