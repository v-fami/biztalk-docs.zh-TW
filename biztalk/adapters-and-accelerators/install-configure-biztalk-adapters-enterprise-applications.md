---
title: "安裝 BizTalk Adapters for Enterprise Applications |Microsoft 文件"
description: "需求和 JD Edwards OneWorld 中，JD Edwards EnterpriseOne，PeopleSoft Enterprise、 TIBCO Rendezvous 和 TIBCO Enterprise Message Service 在 BizTalk Server 上的安裝步驟"
ms.custom: 
ms.date: 10/13/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fa1a09f3d9fa531cee51ecd0e94b99ab972ba13
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2017
---
# <a name="install-and-configure-the-microsoft-biztalk-adapters-for-enterprise-applications"></a>安裝和設定 Microsoft BizTalk Adapters for Enterprise Applications 
  
 Microsoft BizTalk Adapters for Enterprise Applications 包含下列配接器：  
  
-   Microsoft BizTalk Adapter for JD Edwards OneWorld  
  
-   Microsoft BizTalk Adapter for JD Edwards EnterpriseOne  
  
-   Microsoft BizTalk Adapter for PeopleSoft Enterprise  
  
-   Microsoft BizTalk Adapter for TIBCO Rendezvous  
  
-   Microsoft BizTalk Adapter for TIBCO Enterprise Message Service  


> [!IMPORTANT]
> - 進行任何組態變更之前，先備份所有的資料
> - 您必須先熟悉特定企業應用程式進行任何組態變更
  
## <a name="supported-versions--requirements"></a>支援的版本 （& s) 需求

||需求|  
|---|---|
|作業系統|配接器支援與 BizTalk Server 相同的作業系統：<ul><li>[BizTalk Server 2016 需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)</li><li>[BizTalk Server 2013 R2 / 2013年需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md)</li></ul>|
|支援的企業系統|[支援的特定業務 (LOB) 和企業系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)列出支援的版本 |
|JD Edwards OneWorld XE | <ul><li>在 Windows 上的 JD Edwards 企業伺服器</li><li>在 Windows 上的 JD Edwards 部署伺服器</li></ul>|
|JD Edwards EnterpriseOne | 配接器會呼叫 JD Edwards EnterpriseOne API 使用 JDBC 驅動程式所需要的資料庫。 如果您使用 SQL 資料庫安裝 JD Edwards EnterpriseOne，則需要 MS-SQL 驅動程式。 同樣地如果您使用 Oracle 資料庫安裝 JD Edwards EnterpriseOne，您需要 Oracle 驅動程式。或者，如果您安裝與 DB2 資料庫，則需要 DB2 驅動程式。 |
|PeopleSoft Enterprise | <ul><li>Sun Systems Java Development Kit (JDK)</li><li>PeopleSoft 工具版本</li><li>PeopleSoft 應用程式版本</li><li>此配接器需要修改 PeopleSoft 應用程式。 若要使用的元件介面，請將自訂元件介面 GET_CI_INFO 上傳至 PeopleSoft。 GET_CI_INFO.pc 位於 Program Files\Common Files\Microsoft BizTalk Adapters for enterprise \Config\。</li></ul>|
|TIBCO Rendezvous | <ul><li>BizTalk Adapter for TIBCO Rendezvous 執行所在的電腦上必須安裝 TIBCO Rendezvous 執行階段元件</li><li>TIBCO Rendezvous 授權必須設定 BizTalk Adapter for TIBCO Rendezvous 執行所在的電腦上。</li><li>配接器必須能夠看到 TIBCO Rendezvous 二進位檔目錄：在環境變數 PATH 值中，或在 BizTalk Server 中的每個 Rendezvous 連接埠上指定。 這對於 Rendezvous 組件尋找其程式庫和可執行檔是必要的。</li></ul>|
|TIBCO Enterprise Message Service | Enterprise Message Service (EMS) 版本 5.x 及更新版本包含用戶端 SDK （使用 TIBCO EMS C# API）。 BizTalk Adapter for TIBCO EMS 會使用此與伺服器通訊。 |


## <a name="jd-edwards-oneworld-xe"></a>JD Edwards OneWorld XE

此章節包含使用 Microsoft BizTalk Adapter for JD Edwards OneWorld XE 與 BizTalk Server 上的索引鍵資訊。
  
### <a name="create-the-jar-files"></a>建立 JAR 檔案
 本節說明 JD Edwards OneWorld 搭配 Microsoft BizTalk Adapter for JD Edwards OneWorld 使用的需求。  
  
#### <a name="jar-files-and-the-classpath"></a>JAR 檔案和 CLASSPATH  
 JD Edwards OneWorld JAR 檔案必須是可配接器。 比方說，若要連接到 B7.3.3.3 版，會需要下列 jar 檔案。 根據您所連接的伺服器，可能會變更 jar 檔案清單：
  
-   Connector.jar    
-   Kernel.jar  
  
 這些檔案位於 JD Edwards OneWorld 執行所在的電腦上，位置如下：  
  
-   JD Edwards OneWorld XE_install_Directory\System\classes\Connector.jar    
-   JD Edwards OneWorld XE_install_Directory\System\classes\Kernel.jar  
  
 您可以將這些檔案複製到任何位置；不過，您必須在 CLASSPATH 中指定 JAR 檔案的位置。 CLASSPATH 必須包含 JAR 檔案的完整檔案路徑和名稱 (以分號分隔)。  
  
 BizTalk Adapter for JD Edwards OneWorld 提供 JD Edwards OneWorld 搭配 JDEJAccess JAR 檔案。 根據預設，從參考 JDEJAccess.jar 檔案*Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise applications\j.d.edwards。Edwards OneWorld(r) \classes\JDEJAccess.jar*。 
  
> [!NOTE]
>  您必須確認已註冊 jdeinterop.ini 檔案，才能使用 BizTalk Adapter for JD Edwards OneWorld。 請確定您包含在這個檔案的路徑**JDE Transport Property**頁面上，當您在 BizTalk Server 中建立傳送埠。 如需完整說明，請參閱 「 自訂 jdeinterop.ini 檔案。 」  
  
#### <a name="create-the-btslibinteropjar-file"></a>建立 BTSLIBinterop.jar 檔案  
建立檔案，並確認的配接器可以存取它。 您可以使用下列範例做為指南：  
  
1.  建立包含下列程式碼的 BTSLIB.cmd 檔案：  
  
    ```  
    define library BTSLIB  
    login  
    library BTSLIB  
    interface JDEAdapter  
    import B5500900  
    build  
    logout  
    ```  
  
2.  執行下列命令：  
  
    ```  
    GenJava  /cmd  .\BTSLIB.cmd  
    ```  
  
### <a name="verify-your-setup"></a>請確認您的設定  
  
1.  使用支援的版本，包括 service pack 號碼 ([支援的特定業務 (LOB) 和企業系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx))。 Service Pack (ESU 和 ASU) 更新系統二進位檔。 必要的 Service Pack 提供匯入的 ASU/ESU 功能表選項。  
  
2.  設定 jdeinterop.ini 檔案記錄時，使用正確的磁碟機，如果它不同於 c 磁碟機。例如，如果 TEMP 目錄空間不足，可能會失敗 JD Edwards OneWorld 更新。  
  
3.  判斷是否必須針對 JD Edwards OneWorld 欄位的左/右邊框距離加入組態檔。  
  
4.  確認您的 JAVA_HOME 環境變數指向 Java Development Kit (JDK) 安裝，以便從電腦上的任何程式啟用 javac 和 java 命令。  
  
5.  請確認已設定 CLASSPATH 環境變數。 這可讓 BizTalk Adapter for JD Edwards OneWorld 可以找到 Kernel.jar 和 Connect.jar 檔案。  
  
    JAR 檔案的路徑會區分大小寫。  
  
6.  輸入下列區分大小寫的命令來測試環境。  
  
    ```  
    javap -s -p com.microsoft.jde.JDEJAccess  
    ```  
  
7.  您提供的命令 javap 是 Java 類別檔案解譯器：  
  
    ```  
    http://java.sun.com/j2se/1.3/docs/tooldocs/solaris/javap.html  
    ```  
  
8.  `javap`命令會解譯類別檔案。 其輸出取決於所使用的選項。 如果未不使用任何選項，javap 會列印封裝、 受保護，以及公用欄位和類別傳遞給它的方法。 javap 會列印其輸出至 stdout。  
  
     如果沒有任何錯誤，所有 Java 檔案和其相依性會在 CLASSPATH 中。  
  
9. 藉由設定本機主機檔案設定的 DNS 解析 (*C:\WINNT\system32\drivers\etc\hosts*)，JD Edwards OneWorld 系統的伺服器名稱。  
  
### <a name="create-and-install-the-custom-package"></a>建立並安裝自訂封裝  
安裝 BTSREL 自訂封裝，才能使用 BizTalk Adapter for JD Edwards OneWorld。 本章節描述：  
  
-   JD Edwards OneWorld 自訂封裝建立處理程序  
-   如何建立和安裝 BTSREL  
-   JD Edwards OneWorld 中建立的 BTSREL 物件
  
> [!NOTE]
>  BTSREL.exe 是自訂封裝 (以 JD Edwards OneWorld 術語表示則為自動軟體更新或 ASU)。 其中包含可擷取中繼資料的商務功能。 您應該針對特定的 JD Edwards OneWorld 組態和版本來建立自訂封裝。  
  
#### <a name="define-a-custom-package"></a>定義自訂封裝  
 自訂封裝是發行後交付項目，針對特定目的提供軟體變更，例如法規變更或增強功能。 這些自訂封裝會針對特定功能加以建立。 例如，為了擷取中繼資料而建立 BTSREL。 安裝 BTSREL 自訂封裝之後，該封裝會更新 JD Edwards OneWorld 環境中所選取的模組。 若要更新，您必須將 BTSREL 物件併入適當的 JD Edwards OneWorld 環境中。 如需 BTSREL 所更新之模組的詳細清單，請參閱模組清單。  
  
#### <a name="install-the-btsrel-custom-package"></a>安裝 BTSREL 自訂封裝   
下載[BTSREL](https://www.microsoft.com/download/details.aspx?id=56113)。 將它安裝在部署伺服器，然後將它部署至企業伺服器。  
  
 現有的 BTSREL.exe 封裝可直接用於 B7333 版本。 針對封裝用於 B7334 版本，然後：  
  
1.  下載並將 BTSREL.exe 的內容解壓縮到工作資料夾。  
  
2.  修改同時**ReleaseLevelRequired**和**發行**B7334 Deployment.Inf 檔案中的值。  
  
3.  執行安裝程式。  
  
 若要安裝 BTSREL，需要下列條件：  
  
-   部署伺服器安裝    
-   Workbench 安裝  
  
#### <a name="install-btsrel-on-the-deployment-server"></a>在 部署伺服器上安裝 BTSREL  
 自訂封裝僅適用於 Windows 作業系統，並使用與部署伺服器。 它必須建置在部署伺服器，並接著部署至企業伺服器。 企業伺服器通常是實際執行伺服器，可以位於 Windows 或 UNIX 作業系統上。  
  
> [!NOTE]
>  將 asu 套用至 JD Edwards OneWorld 部署伺服器，請確認您是在**更新**模式。 **證明**模式可確認 ASU 中沒有任何錯誤而**更新**模式會指定適用於在套用 ASU 時。  
  
1.  部署伺服器以使用者身分登入**JDE**。  
  
2.  在部署伺服器 (根目錄) 的 /B7 資料夾中，建立新的資料夾 BTSREL。  
  
3.  將 BTSREL.exe 複製到新建立的 BTSREL 資料夾。  
  
4.  從 .../B7/BTSREL 資料夾執行 BTSREL.exe。 安裝管理員會自動啟動。  
  
5.  在 [安裝] 視窗中，選取**下一步**，然後選取**完成**。 如果安裝成功，則會顯示訊息。  
  
6.  登入 JDEPLAN 環境為**JDE** JD Edwards OneWorld 部署伺服器上的使用者。  
  
    1.  如果系統上未安裝含有 SAR # 4533357 的電子軟體更新 (ESU)，選取**軟體更新**從**系統安裝工具**功能表 (GH9612)。  
  
    2.  選項 1 中，輸入 02**處理選項**面板。  
  
    3.  如果已安裝含有 SAR # 4533357 ESU 系統上，選取**應用程式的軟體更新**從**系統安裝工具**功能表 (GH9612)。  
  
#### <a name="install-btsrel-on-the-jd-edwards-oneworld-workbench"></a>在 JD Edwards OneWorld WorkBench 上安裝 BTSREL  
   
1.  在**搭配應用程式更新**畫面上，按兩下 BTSREL 更新，並選取**下一步**。  
  
2.  按兩下您想要安裝、 更新的環境，然後選取**下一步**。  
  
    1.  請檢查**Unattended Workbench**如果您想要在自動模式中執行的軟體更新。  
  
    2.  選取**備份**如果您想要備份規格 （如此可以還原原始規格）。  
  
3.  在**搭配安裝計劃**畫面上，選取您要安裝的更新的計劃，然後**選取**。  
  
4.  安裝完成之後，請查看自動產生的 PDF 是否有任何錯誤。  
  
    > [!NOTE]
    >  如果發生錯誤，請參閱「JD Edwards OneWorld 軟體更新指南」中的疑難排解秘訣，或直接連絡 JD Edwards OneWorld。  
  
5.  手動註冊商務功能程式庫，使用 「 手動註冊商務功能程式庫 」 這一節中的步驟。  
  
#### <a name="uninstall-the-custom-package"></a>解除安裝自訂封裝  
 解除安裝自訂封裝沒有任何需求。 不過，如果您想要清理系統，您可以使用不同的方式來解除安裝。 解除安裝之後，重建封裝使用下列方法之一：  
  
-   使用 JD Edwards OneWorld 部署伺服器，Gh8612 — P96470 上**列**功能表上，選取**更新**，然後選取**解除安裝**。    
-   核取並刪除用戶端電腦上的所有自訂物件 (BTSREL)。    
-   套用先前的資料庫快照集。  
  
 在清除期間，確認 JD Edwards OneWorld 的其他物件是否有任何其他修改。  
  
#### <a name="manually-register-the-business-function-library"></a>手動註冊商務功能程式庫  
 由於 JD Edwards OneWorld 產品封裝程序的限制，您必須向 JD Edwards OneWorld 手動註冊 BizTalk Adapter for JD Edwards OneWorld 的自訂商務功能程式庫 DLL。 這個程序包含下列步驟。
  
##### <a name="step-1-create-the-custom-business-function-library"></a>步驟 1： 建立自訂商務功能程式庫  
 使用 JD Edwards OneWorld Object Management Workbench (OMW) 建立自訂商務功能程式庫。 下列程序必須在初始設定，執行，而且適用於所有平台。  
  
1.  啟動 Object Management Workbench (快速路徑:"OMW"或功能表選項： GH902 物件： P98220)。  
  
2.  選取**新增**，然後選取的選項**商務功能程式庫**。  
  
3.  輸入新商務功能程式庫物件的下列資訊：  
  
    -   **名稱：** ACBLIB    
    -   **描述：** Microsoft DLL    
    -   **產品代碼：** 55    
    -   **產品系統程式碼：** 55  
  
4.  選取 [確定]。  
  
##### <a name="step-2-rebuild-libraries-from-the-deployment-server"></a>步驟 2： 重建程式庫，從部署伺服器  
完成下列步驟在每個平台的初始設定。  
  
1.  若要在獨立模式下啟動 BusBuild 程式，選取**啟動**，選取**執行**，然後選取**busbuild.exe**。
  
2.  以 pathcode （PY7333、 PD7333 或 DV7333） 登入 JD Edwards OneWorld。  
  
3.  在**重建程式庫**清單中，選取**建置**。  
  
##### <a name="step-3-copy-the-custom-dll"></a>步驟 3： 複製自訂 DLL  
 將自訂 DLL 從 pathcode 目錄複製到 JD Edwards OneWorld 部署伺服器和 JD Edwards OneWorld 企業伺服器上的父封裝目錄。
  
**JD Edwards OneWorld XE 部署伺服器上**  
  
1.  將 ACBLIB.dll 從 DV7333\bin32 複製到 DV7333\Packages\DV7333FA\bin32。  
  
2.  將 ACBLIB.def、ACBLIB.dmp 和 ACBLIB.mak 從 DV7333\obj 資料夾複製到 DV7333\Packages\DV7333FA\obj 資料夾。  
  
3.  ACBLIB.exp、 ACBLIB.lib 和 sACBLIB.lib DV7333\lib32 將資料夾複製到 DV7333\Packages\DV7333FA\lib32 資料夾。  
  
**JD Edwards OneWorld 企業伺服器上**  
  
建立每個目錄和檔案之後，確認授權。  
  
1.  建立目錄 ACBLIB 下 DV7333FA\obj\\。  
  
2.  建立目錄 ACBLIB DV7333FA\source 底下。  
  
3.  將 b5500900.c 從部署伺服器的 DV7333\source 目錄傳送至 DV7333FA\source\ACBLIB 目錄。  
  
4.  從部署伺服器 DV7333\include 目錄 FTP b5500900.h DV7333FA\include 目錄。  
  
##### <a name="step-4-build-a-full-package"></a>步驟 4： 建置完整封裝  
 由於 JD Edwards 封裝建置程序的限制，建置完整封裝的環境中要套用 BTSREL 更新，或更新封裝組建無法正常運作。 請參閱 JD Edwards 說明，以了解如何建置完整封裝組建。  
  
> [!NOTE]
>  當您套用 JD Edwards OneWorld ASU/ESU 時，ASU/ESU 通常不會建立新的程式庫和商務功能。 因此，處理程序很簡單： 但是，BizTalk Adapter for JD Edwards OneWorld 自訂封裝會建立新的程式庫。 因此，您必須執行額外的步驟，例如，手動建立目錄，並執行完整封裝組建。  
  
#### <a name="modules-list"></a>模組清單  
 BTSREL 自訂封裝會在 JD Edwards OneWorld 中建立下列物件。 BTSREL 包含可擷取中繼資料的商務功能，以及可測試資料類型的自訂功能。  
  
> [!NOTE]
>  JD Edwards OneWorld 更新有一個 Bug。 如果您不需要所有的商務和自訂函式，請確認完整封裝組建已完成，而不是更新封裝組建。  
>  
>  如果您遺漏清單中的檔案，例如，如果您具有 ACBTEST 下方的所有檔案但遺漏上方的檔案，則可能遺漏「資料字典」(DD) 項目。 您可以移至**Work With Data Items**並尋找遺漏的檔案。  
>   
>  如果您遺漏其他項目，例如 ACBCHAR01、 ACBDATE01、 ADBINT01、 ACBMATH01 和 ACBSTR01，這些是*主要資料元素*。 當您合併從規劃到開發的物件時，會在背景執行許多報表。 您可以開啟合併報表並尋找是否有任何錯誤。 報表應該列出所有項目，並指出已完成且沒有任何錯誤或警告。 透過這項驗證，由於所有項目都已計入，因此您可以繼續進行。  
  
-   ACBCHAR01 - 測試 CHAR 類型 01  
  
-   ACBCUST - ACB 客戶識別碼  
  
-   ACBDATE01 - 測試日期類型 01  
  
-   ACBDEF - ACB 功能類型定義  
  
-   ACBFCNT - ACB 功能名稱清單計數  
  
-   ACBFUNC-ACB 函式名稱清單  
  
-   ACBFUNCN-ACB 函式名稱  
  
-   ACBINT01 - 測試整數類型 01  
  
-   ACBLIB - 控制 BROKER 程式庫  
  
-   ACBMATH01 - 測試數學類型 01  
  
-   ACBNEWS - ACB 新狀態  
  
-   ACBORDER - ACB 訂單號碼  
  
-   ACBPRC - ACB 項目價格  
  
-   ACBPROD - ACB 產品識別碼  
  
-   ACBQTY - ACB 項目數量  
  
-   ACBRES - ACB 結果指標  
  
-   ACBSTAT - ACB 狀態  
  
-   ACBSTR01 - 測試字串類型 01  
  
-   ACBTEST - ACB 測試畫面  
  
-   ACBTEST2-ACB 測試畫面 2  
  
-   ACBTEST3-ACB 測試畫面 3  
  
-   B5500900 - 控制 BROKER 支援模組  
  
-   D5500900-控制 BROKER 資料結構  
  
-   D5500900A-控制 BROKER 資料結構  
  
-   D5500900B-提取價格資料結構  
  
-   D5500900C - 取得客戶狀態資料結構  
  
-   D5500900D-組客戶狀態資料結構  
  
-   D5500900E-更新銷售訂單狀態資料結構  
  
-   D5500900F - 測試整數  
  
-   D5500900G-測試字串  
  
-   D5500900H-測試日期  
  
-   D5500900I-測試 CHAR  
  
-   D5500900J - 測試數學數值  
  
-   D5500900K-測試日期 2  
  
#### <a name="customize-the-jdeinteropini-file"></a>自訂 jdeinterop.ini 檔案  
 Connector.jar 和 Kernel.jar 中的 JD Edwards OneWorld XE 連接器類別會要求您使用 jdeinterop.ini 的組態檔。 這個檔案由 JD Edwards OneWorld 軟體所定義，並使用其術語。 JD Edwards 互通性手冊發行 OneWorld 可能提供之用途和術語，這個檔案的詳細資訊。 沒有範例 jdeinterop.ini 檔案*< 可 > \config\jde*。  
  
更新以符合您在中定義的參數值的 jdeinterop.ini**傳輸屬性**螢幕。 如果其參數相容，則多個 JD Edwards OneWorld 邏輯系統可以共用同一個 jdeinterop.ini 檔案。 一般而言，如果兩個邏輯系統指向兩部不同的 JD Edwards OneWorld 電腦，它們需要兩個不同的 jdeinterop.ini 複本。  
  
> [!NOTE]
>  Jdeinterop.ini 中的記錄應該關閉，並可以放心地忽略各種記錄檔的參數。  
  
 下表逐項列出位於 jdeinterop.ini 檔案中的設定， 並依區段分組其資訊。 例如，[JDENET] 等區段會依其在 JD Edwards OneWorld 軟體中出現的順序列出。  
  
#### <a name="jdeinteropini-file-settings"></a>jdeinterop.ini 檔案設定
  
|章節|參數和描述|  
|-------------|-------------------------------|  
|[JDENET]|**EnterpriseServerTimeout。** 企業伺服器要求的逾時值，以毫秒為單位。 預設大小是 120000。<br /><br /> **Sqlserversink。** JDENET 通訊端連接集區大小。 預設大小為 30。|  
|[SERVER]|**glossaryTextServer。** 提供詞彙文字資訊的企業伺服器和連接埠。 這是傳回錯誤文字描述的伺服器。 通常是與 JD Edwards OneWorld 應用程式伺服器相同的主機和連接埠。 為了支援不同的語言編碼，可能會有多個詞彙伺服器。 例如，JDED:6010 或 actsrv1:6009。 這些值必須符合在 [系統定義] 中設定的值。<br /><br /> **字碼頁。** 編碼配置中。 預設為 1252年。<br /><br /> 1252 英文和西歐語系<br /><br /> -932 日文<br /><br /> -950 繁體中文<br /><br /> -936 中文 （簡體的)<br /><br /> -949 韓文|  
|[記錄檔]|**記錄檔 = c:\jas.log。** 記錄檔的位置。 您可以放心地略過這個參數。<br /><br /> **debuglog = c:\jasdebug.log。** 偵錯記錄檔的位置。 您可以放心地略過這個參數。<br /><br /> **偵錯。** 判斷是否開啟 JDENET 偵錯功能。 預設值為 FALSE。|  
|[DEBUG]|**JobFile = c:\Interop.log。** 錯誤檔的位置。 您可以放心地略過這個參數。<br /><br /> **DebugFile = c:\InteropDebug.log。** 偵錯檔案的位置。 您可以放心地略過這個參數。<br /><br /> **記錄檔 = c:\net.log。** 記錄檔的位置。 您可以放心地略過這個參數。<br /><br /> **debugLevel = 0-12。** 偵錯層級。 您可以放心地略過這個參數。 這會定義指定記錄檔中 COM 連接器和 Callobject 元件所提供的追蹤層級，僅適用於 COM 伺服器。<br /><br /> -無 0。 關閉記錄功能並僅將錯誤寫入 JobFile。<br /><br /> -2 的錯誤 （錯誤訊息）<br /><br /> -4 系統錯誤 （例外狀況訊息）<br /><br /> -6 警告資訊<br /><br /> -8 最小追蹤 （索引鍵作業。 例如登入、 登出、商務功能呼叫)。<br /><br /> -10 的疑難排解資訊 （說明）。<br /><br /> -12 完整的偵錯資訊 （記錄檔的所有項目）<br /><br /> -根據預設，您不必開啟追蹤功能，但在偵錯您的程式碼時，追蹤就很有用。<br /><br /> -NetTraceLevel = 0。 追蹤層級。 您可以放心地略過這個參數。 定義在指定的記錄檔中，COM 伺服器 ThinNet 元件所提供的追蹤層級。 奇數值則保留給未來要加入的層級。<br /><br /> -下列清單描述更多偵錯層級：<br /><br /> -0 無追蹤<br /><br /> -1 表示記錄處理序識別碼、 執行緒識別碼和可用的通訊端狀態時加入新的連接，並搜尋通訊端集區。<br /><br /> -2 包含追蹤層級 1 中的資訊，也會追蹤連接管理員類別中所做的每個呼叫。<br /><br /> -3 包含追蹤層級 2，以及追蹤 getport （） 呼叫和 gethost （） 呼叫中的所有資訊。|  
|[INTEROP]|**enterpriseServer。** 這個值是主機伺服器的名稱。 請確定此值是您在中輸入的相同值**主機名稱**欄位**JDE [Credentials**一節中**系統定義**中**傳輸屬性**] 對話方塊。 預設為 JDED。<br /><br /> **連接埠。** 這個值是用來交換資料的連接埠編號。 請確定此值是您在中輸入的相同值**連接埠號碼**欄位在 JD Edwards**認證**一節中**傳輸屬性 系統定義**. 例如，6010 或 6009。 在中設定這些值必須符合**系統定義**。<br /><br /> **inactive_timeout**。 自動認可模式下的交易逾時值，以毫秒為單位。 如果使用者在這段時間 (毫秒) 內沒有活動，interop 伺服器會將使用者登出。 您可以將這個值變更為更短的時間。 預設為 1200000。<br /><br /> **manual_timeout。** 以毫秒為單位，在手動認可模式下的交易逾時值。 預設為 120000。<br /><br /> **儲存機制。** 指向包含 Connector.jar 和 Kernel.jar 的目錄位置。 在 UNIX 上，這是完整路徑。|  
|[CORBA]|您可以放心地略過這個參數。<br /><br /> **多執行緒。** 您可以忽略此設定。 設定為 1 表示提供多執行緒支援給 CORBA。<br /><br /> Objects= CORBA::Connector;CORBA::OneWorldVersion<br /><br /> 為 CORBA 伺服器定義要在啟動時建立的物件。 也會取代-DIORFILENAME = 命令列選項，例如： CORBA::Connector=connector.ior。|  
  
## <a name="jd-edwards-enterpriseone"></a>JD Edwards EnterpriseOne  
此章節包含使用 Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 與 BizTalk Server 上的索引鍵資訊。
  
### <a name="execute-a-jd-edwards-enterpriseone-master-business-function"></a>執行 JD Edwards EnterpriseOne 主要商務功能  
 您可以使用 BizTalk Adapter for JD Edwards EnterpriseOne 來叫用 JD Edwards EnterpriseOne 主要商務功能，例如通訊錄、 採購單或銷售訂單。 您也可以使用這個配接器來連接 JD Edwards EnterpriseOne 和 BizTalk Server，以進行整合。  
  
##### <a name="access-data-stored-in-jd-edwards-enterpriseone"></a>存取 JD Edwards EnterpriseOne 中儲存資料  
 此配接器接受 XML 訊息，讓 BizTalk Server 應用程式進行通訊，並與 JD Edwards EnterpriseOne 使用下列其中一項交換的交易：  
  
-   **傳輸配接器**，其中使用靜態請求-回應傳送埠將訊息傳送至 JD Edwards EnterpriseOne 並預期回應。    
-   **接收配接器**，使用靜態單向接收埠來接收 JD Edwards EnterpriseOne 的訊息。  
  
### <a name="interoperability-framework"></a>互通性架構  
 JD Edwards EnterpriseOne 透過其互通性架構提供與系統的整合。 配接器會使用 JD Edwards EnterpriseOne 架構，並利用各種整合存取方法，以提供最大的彈性和功能。  
  
 BizTalk Adapter for JD Edwards EnterpriseOne 支援下列整合存取方法：  
  
-   JD Edwards EnterpriseOne ThinNet API    
-   JD Edwards EnterpriseOne XML    
-   JD Edwards EnterpriseOne 未編輯的交易資料表 (Z 資料表)  
  
 這個配接器使用 JD Edwards EnterpriseOne ThinNet API 與 JD Edwards EnterpriseOne 應用程式通訊。 透過 ThinNet API，這個配接器可以在單一工作單元 (UOW) 中叫用一個主要商務功能 (MBF)。 當 MBF 失敗時，整個 UOW 都會失敗。 如此可防止部分更新。 JD Edwards EnterpriseOne 應用程式會處理基礎資料庫的資料、商務規則和通訊的驗證。  
  
#### <a name="jd-edwards-outbound-processing-framework"></a>JD Edwards 輸出處理架構  
 在輸出程序中，當特定 MBF 在 JD Edwards EnterpriseOne 環境中執行時，便會啟動這個事件。 MBF 會將事件的必要資訊寫入適當的介面資料表，然後通知子系統批次功能 (BF) 有此事件發生。 子系統 BF 接著會在子系統資料佇列中加入該事件的項目。  
  
 輸出子系統會擷取資料佇列項目，並查詢「資料匯出控制」資料表中是否有需要通知的外部處理序。 輸出子系統接著會呼叫 BizTalk Adapter for JD Edwards EnterpriseOne 接聽程式，並提供通知。 接聽程式會將通知傳遞給產生器。 產生器接著會使用 JD Edwards EnterpriseOne ThinNet API 來擷取介面資料表中的適當資訊。  
  
### <a name="set-string-justification-in-jdearglist"></a>在 Jdearglist 中設定字串左右對齊  
 若要將一些字串引數設定為靠右對齊和左填補中 J.D. Edwards EnterpriseOne jdearglist.txt 檔案中，您必須知道您想要存取;具體來說，您必須知道您想要呼叫的商務功能中的哪些欄位。  
  
 您必須先更新 jdearglist.txt，然後才能在協調流程中產生繫結 (結構描述)。 更新 jdearglist.txt 檔案中 < 處理字串值 > 一節所述的指示。  
  
 如果您在記錄檔中收到 jdearglist.txt 警告訊息，其目的是通知您，找不到 jdearglist.txt。 不過，如果您執行 SalesOrder 或 PurchaseOrder 商務功能，您必須擁有該檔案在路徑中或無法運作。  
  
### <a name="understand-jdeinteropini"></a>了解 jdeinterop.ini  
 Connector.jar 和 Kernel.jar 中的 JD Edwards EnterpriseOne 連接器類別會要求您使用名為 jdeinterop.ini 的組態檔。 這個檔案是由 JD Edwards EnterpriseOne 軟體所定義，並使用其術語。 如需這個檔案之用途和術語的詳細資訊，請參閱 "JD Edwards Interoperability Guide"。 沒有範例 jdeinterop.ini 檔案： Program Files\ Microsoft BizTalk Adapters for Enterprise Applications\ J.D. Edwards EnterpriseOne(r) \config。  
  
 不建議您先手動編輯此檔案因為與它互動**傳輸屬性**對話方塊的 傳送埠，例如這些欄位標記為  **< by Biztalk>\>**.  
  
## <a name="peoplesoft-enterprise"></a>PeopleSoft Enterprise  
本節包含使用 Microsoft BizTalk Adapter for PeopleSoft Enterprise 與 BizTalk Server 上的索引鍵資訊。
  
### <a name="receive-handler-peoplesoft-requirements"></a>接收處理常式 PeopleSoft 需求  
 PeopleSoft Integration Broker 必須能夠與 BizTalk Server 通訊。 現有的 PeopleSoft 環境中可能已發生下列情況，而且您可能會重複使用現有的節點；因此，除了向 PeopleSoft 系統管理員取得 HTTP 規格，您不必執行任何動作。 如需詳細資訊，請參閱 PeopleSoft 文件。  

下列步驟概述在 PeopleSoft 中完成：  
  
1.  設定訊息，並讓它成為透過應用程式的設計工具。  
  
2.  對 PeopleSoft integration.gateway.properties 檔案進行一次性變更。  
  
3.  建立並設定閘道和節點，以啟用 HTTP:
  
    -   這個節點必須使用一些觸發方法，例如 LOCATION_SYNC 機制。   
    -   這個節點必須使用 HTTP。    
    -   這個節點必須指向傳送事件的目標主機和連接埠。  
  
### <a name="send-handler-peoplesoft-requirements"></a>傳送處理常式 PeopleSoft 需求  
 BizTalk Adapter for PeopleSoft Enterprise 可讓您透過 Java API 存取的自訂元件介面 (CI) 所組成。 自訂 CI 物件**GET_CI_INFO**，部署在 PeopleSoft 系統提供的中繼資料資訊所需的 BizTalk Adapter for PeopleSoft Enterprise 使用 PeopleSoft 工具。 如需詳細資訊，請參閱 PeopleSoft 文件。  
  
 上載自訂元件介面的動作只發生一次。 GET_CI_INFO.pc 這個檔案隨附於產品，必須安裝在 PeopleSoft 系統中，才能使用配接器瀏覽 CI。 您必須能夠存取 PeopleSoft 應用程式設計工具中。不過，在 應用程式設計工具沒有位於任何位置附近的 BizTalk Server 電腦。 您可以使用 應用程式設計工具來將自訂 CI 上傳到您瀏覽的 PeopleSoft 電腦。  
  
 您必須有 PeopleSoft 電腦的存取權，因為您必須設定環境變數 CLASSPATH (或設定資訊**傳輸屬性**視窗) 以指向 PeopleSoft PSJOA/psjoa.jar 檔案。  
  
### <a name="set-environment-variable-and-use-component-interface"></a>設定環境變數，並使用元件介面  
如需 PeopleSoft 的詳細資訊，請參閱 PeopleSoft 文件。  
  
#### <a name="set-classpath-environment-variable"></a>設定 ClassPath 環境變數  

**更新 JAVA_HOME**    
  
 請將 JAVA_HOME 變數設定為指向 JDK 安裝，例如：  
  
```  
set JAVA_HOME=C:\j2sdk1.4.2_06  
```  
  
 **更新 CLASSPATH**  
  
若要使用元件介面 (PeopleSoft 8) 則必須更新 CLASSPATH 來包含 PeopleSoft 元件介面 jar 檔案：
  
1.  在**控制台**，開啟**系統**。  
  
2.  在**進階**索引標籤上，選取**環境變數**，然後選取**CLASSPATH**。  
  
3.  新增路徑。 例如，輸入：  
  
    ```  
    <PeopleSoft_Home>\web\PSJOA\psjoa.jar  
    ```  
  
 BizTalk Adapter for PeopleSoft Enterprise 需要 psjoa.jar 檔案。 當您建立傳送埠時會執行這項作業。 如需詳細資訊，請參閱配接器文件中的 "Setting Transport Properties in PeopleSoft System"。  
  
> [!NOTE]
>  僅在您的 PATH 中使用其中一個目錄，以確保 BizTalk Adapter for PeopleSoft Enterprise 選取正確的 DLL。 未能正確設定所需 PeopleSoft 版本的環境，可能會導致錯誤很難追蹤。  
  
#### <a name="use-component-interfaces"></a>使用元件介面  
  
<a name="BKMK_CustomCI"></a>   
##### <a name="upload-a-custom-ci-into-peoplesoft"></a>將自訂 CI 上傳至 PeopleSoft  
 BizTalk Adapter for PeopleSoft Enterprise 需要修改 PeopleSoft 應用程式。 若要使用元件介面，您必須將自訂元件介面 GET_CI_INFO 上傳至 PeopleSoft。 您只需要在初始設定期間匯入 GET_CI_INFO，即可使用配接器。 這個配接器使用 GET_CI_INFO 來取得 PeopleSoft 中其他現有元件介面的相關資訊。  
  
 本節說明如何以手動方式匯入自訂元件介面，可讓您瀏覽 PeopleSoft 中的元件介面。 請注意，不使用或修改任何屬性，它會安裝在元件介面的自訂方法。 若要匯入自訂元件介面，您可以使用下列其中一個方法：  
  
-   建立新的元件以匯入自訂方法。  
  
-   使用不含索引鍵的現有元件，例如 INSTALLATION_RS。  
  
 簡單的元件介面不能包含索引鍵。 如果您不確定特定元件介面是否包含索引鍵，您可以使用 SQL 查詢工具執行這個簡單的 SQL 陳述式。 它可讓您在應用程式中所有不含索引鍵的元件介面清單。  
  
```  
select distinct BCNAME  
from PSBCITEM bc1  
where not exists  
(select 1  
from PSBCITEM bc2  
where bc1.BCNAME = bc2.BCNAME  
and bc2.BCTYPE in (1, 2))  
```  
  
 您可以遵循 PeopleSoft 文件，建立唯一的簡單元件來儲存 BizTalk Adapter for PeopleSoft Enterprise 的自訂方法。 您也可以複製其中一個已存在的元件介面，並使用它來儲存自訂方法。  
  
 若要確認您的 GET_CI_INFO 不含索引鍵，請執行 PeopleTools Application Designer 元件介面測試工具。  
  
<a name="BKMK_NewCom"></a>   
##### <a name="create-a-new-component-interface"></a>建立新元件介面  
 請遵循下列步驟來建立新元件介面使用的 PeopleSoft 應用程式設計工具 中：
  
1.  開啟**PeopleSoft 應用程式設計工具**。  
  
2.  輸入三層式連接類型，然後再按一下**確定**。 例如，從清單中選取 [Application Server]。  
  
3.  在 應用程式設計工具中，在**檔案**功能表上，選取**新增**。  
  
4.  在**新增**對話方塊中，選取**元件介面**，然後按一下**確定**。  
  
5.  按一下 [選取]。  
  
6.  從所有元件清單中選取任何簡單的元件。 例如，選取 INSTALLATION_RS 或您建立的新 PeopleSoft 元件。  
  
 自訂方法不會使用或修改安裝所在之元件介面的任何屬性。  
  
 這個簡單的元件介面不能包含索引鍵。 如果您不確定特定元件介面是否包含索引鍵，您可以使用 SQL 查詢工具執行這個簡單的 SQL 陳述式。 它可讓您在應用程式中所有不含索引鍵的元件介面清單：  
  
```  
select distinct BCNAME from PSBCITEM bc1 where not exists (select 1 from PSBCITEM bc2 where bc1.BCNAME = bc2.BCNAME and bc2.BCTYPE in (1, 2))  
```  
  
> [!NOTE]
>  您也可以遵循 PeopleSoft 文件，建立唯一的簡單元件來儲存 BizTalk Adapter for PeopleSoft Enterprise 的自訂方法。  
  
 若要確認您的 GET_CI_INFO 不含索引鍵，請執行 PeopleTools Application Designer 元件介面測試工具。  
  
##### <a name="check-component-interface"></a>檢查元件介面  
 您已完成將 Microsoft BizTalk Adapter for PeopleSoft GET_CI_INFO 上傳至 PeopleSoft 系統。 GET_CI_INFO 是使用者定義的自訂元件介面， 它包含使用者定義的方法。 GET_CI_INFO 元件介面可讓您使用 Microsoft Adapter 精靈瀏覽 PeopleSoft 系統中的元件介面。 您可以尋找並展開 GET_CI_INFO，以檢視其使用者定義的方法。  
  
> [!NOTE]
>  如需使用者定義方法的詳細資訊，請參閱配接器文件中的 「 PeopleSoft:: 元件介面使用者定義方法 」。  
  
##### <a name="set-the-component-interface-security"></a>設定元件介面安全性  
 在 PeopleSoft 上安裝自訂 GET_CI_INFO PeopleSoft 元件介面之後，設定的安全性設定**GetCINamespace**， **GetDetails**，和**GetCollections**BizTalk Adapter for PeopleSoft Enterprise 的方法。 這是建立自訂元件或使用者定義方法時的標準作法。  
  
> [!NOTE]
>  下列程序說明如何在所有支援的模式下，為所有支援的 PeopleSoft 版本設定安全性。  
>   
>  設定元件介面的安全性  
  
1.  指向**PeopleTools**，指向 **安全性**，指向  **Permissions & Roles**，然後選取**Permission Lists**。  
  
2.  在**Maintain Security**視窗中，按一下 **搜尋**，選取相關**權限清單**，然後按一下適當的清單超連結。  
  
3.  在**權限清單**窗格的右邊按一下向右箭號旁**sign-on Times**索引標籤，顯示**元件介面** 索引標籤。  
  
4.  按一下**元件介面** 索引標籤。  
  
5.  按一下加號 （+），加入新的資料列以**元件介面**清單。  
  
6.  選取**GET_CI_INFO**元件介面，然後再按一下**編輯**。  
  
7.  若要將方法設定為**完整存取**，按一下**Full Access (All)**，然後按一下 **[確定]**。  
  
8.  捲動至底部**元件介面**視窗中，然後再按一下**儲存**。  
  
##### <a name="test-the-component-interface"></a>測試元件介面  
 您已完成設定 BizTalk Adapter for PeopleSoft Enterprise 所提供之 GET_CI_INFO 元件介面的安全性。 您的 PeopleSoft 元件介面已就緒，可供您瀏覽 PeopleSoft 元件介面。  
  
 請執行下列步驟，在 Application Designer 中測試元件介面。  
  
 若要測試元件介面  
  
1.  啟動**PeopleSoft 應用程式設計工具**。  
  
2.  在**檔案**功能表上，指向**開啟**，然後選取**定義 = Component Interface**。  
  
3.  從元件介面清單中，選取**GET_CI_INFO CI**。  
  
4.  開啟 GET_CI_INFO 之後，以滑鼠右鍵按一下您的元件介面定義右窗格中的任何位置，然後選取**Test Component Interface**。  
  
**Component Interface Tester**視窗隨即開啟。 並且應該不會列出任何索引鍵。 如果您的 GET_CI_INFO 包含索引鍵，或者選取另一個選項，返回 應用程式設計工具中，並清除 GET_CI_INFO 中的所有索引鍵。  
  
## <a name="install-steps"></a>安裝步驟
 在安裝之前，確定 BizTalk Server 而且必須先安裝配接器的所有軟體必要元件。 建議您關閉所有應用程式，再執行安裝程式。  
  
1.  執行 BizTalk Server **Setup.exe**，選取**安裝 Microsoft BizTalk Adapters**，然後選取**安裝 Microsoft BizTalk Adapters for Enterprise Applications**。  
  
    > [!NOTE]
    >  - 您也可以執行無訊息安裝中使用下列命令： msiexec /i < msi\> /qn /l* < 記錄檔\>-其中 < 記錄檔\>是選擇性的但發生安裝失敗時很有用。  
    >  - 安裝會更新 PATH 環境變數。 若要確定您使用的變數正確，請關閉安裝命令視窗以更新變數。  
  
2.  接受**合約**，然後選取**下一步**。
  
3.  輸入您**客戶資訊**，然後選取**下一步**。  
  
4.  選取**完成**或**自訂**安裝： 
  
    -   **完成**： 安裝 Microsoft BizTalk Adapters for Enterprise Applications，所有的程式功能，並用它來開發和執行階段。  
  
    -   **自訂**： 您選擇的介面卡和您想要安裝，而且安裝所在的功能。  
  
    若要設定目的地，請選取**瀏覽**，並設定安裝路徑。  
  
    選取**下一步**才能繼續。  
  
5. **安裝**，然後選取**完成**時完成。  
  
> [!IMPORTANT]
>  在安裝期間，您可能會遇到下列錯誤：  
>   
>  `Error 1609. An error occurred while applying security settings. CREATOR OWNER is not a valid user or group`  
>   
>  若要解決這個錯誤，執行下列工作，並再次執行安裝程式：  
>   
>  1. 開啟命令提示字元
>  2. 類型： `net user "CREATOR OWNER" /add`。 這會建立新的使用者 CREATOR owner。
>  3. 類型： `net localgroup Users /add`。 這會建立名為使用者的新群組。
  
若要新增的配接器至 BizTalk Server，請參閱 「 新增配接器給 BizTalk 系統管理員 」 本主題中。

## <a name="add-adapters-to-biztalk-admin"></a>將配接器加入至 BizTalk 系統管理員
  
> [!NOTE]
>  如果您安裝 BizTalk （某部電腦上，執行階段專用的安裝和管理僅限工具安裝在另一部電腦上） 在多重電腦環境中，您應該安裝為企業應用程式的 BizTalk 配接器在電腦上。  
  
1.  開啟 BizTalk Server 管理主控台中，展開**Microsoft BizTalk Server**，然後展開**平台設定**。  
  
2.  以滑鼠右鍵按一下**配接器**，選取**新增**，然後選取**配接器**。  
  
3.  輸入名稱，例如**PeopleSoft**。  
  
4.  選取從您輸入的名稱**配接器**清單，並選取**確定**。  
   
## <a name="post-install---jd-edwards-oneworld"></a>後續安裝-JD Edwards OneWorld  
 Microsoft BizTalk Adapter for JD Edwards OneWorld 介面支援的資料庫與 Microsoft BizTalk server 的伺服器系統傳輸配接器所組成。 傳輸配接器可讓您叫用從 BizTalk Server 的伺服器系統的呼叫。 傳輸配接器 (BizTalk Server 管理傳送處理常式) 組態會指定 SQL 資料庫的位置。  
  
 請參閱有關如何使用 BizTalk Adapter for JD Edwards OneWorld 以及其模型與 BizTalk Server 模型之間的對應資訊的配接器文件。  
  
### <a name="single-sign-on"></a>單一登入 (SSO)  
 BizTalk Adapter for JD Edwards OneWorld 提供支援的企業單一登入 (SSO)。 如果您選取使用在 SSO**傳輸屬性**頁面上，認證會使用 SSO 認證資料庫中的分支機構應用程式。 分支機構應用程式代表需要認證的後端應用程式。  
  
### <a name="installed-components"></a>已安裝的元件  

* 配接器安裝會安裝並註冊下列元件在全域組件快取 (GAC) 中。 您可以確認註冊在檔案總管中開啟組件資料夾 (< %WINDIR%> \assembly)，或使用`gacutil /l`從 Visual Studio 命令提示字元：

    -   Microsoft.BizTalk.Adapters.BizUtil.dll    
    -   Microsoft.BizTalk.Adapters.JDEProperties.dll    
    -   Microsoft.BizTalk.Adapters.CoreManagement.dll    
    -   Microsoft.BizTalk.Adapters.CoreReceiver.dll    
    -   Microsoft.BizTalk.Adapters.CoreTransmitter.dll  

  
* btsTask.exe 會安裝和部署`Microsoft.BizTalk.Adapters.JDEProperties.dll`檔案到 GAC。 BizTalk Server 部署記錄結果位於*\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\jdeDeploy.html*和**jdeDeploy.xml**。
  
* 配接器特定的檔案會安裝在*Program Files*和*Program Files\Common Files*。  
  
* `sdk\`安裝在*Program Files\Microsoft BizTalk Adapters for Enterprise Applications\ J.D.Edwards OneWorld(r)*。
  
* * 程式 Files\Microsoft BizTalk Adapters for Enterprise Applications\JD Edwards OneWorld(r)\*包含下列檔案：  
  
    -   classes\JDEJAccess.jar    
    -   Config\ J.D. Edwards OneWorld(r) \BTSREL.exe    
    -   Config\ J.D. Edwards OneWorld(r) \jdearglist.txt    
    -   Config\ J.D. Edwards OneWorld(r) \jdeinterop.ini  
  
* * 程式 Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\Bin\*包含下列檔案：  
  
    -   Microsoft.BizTalk.Adapters.JDEProperties.dll    
    -   jdecba.dll  
  
## <a name="post-install---jd-edwards-enterpriseone"></a>後續安裝-JD Edwards EnterpriseOne  
 Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 包含傳輸配接器，可與支援的資料庫和 BizTalk server 的伺服器系統。 傳輸配接器可讓您叫用從 BizTalk Server 的伺服器系統的呼叫。  
  
 BizTalk Adapter for JD Edwards EnterpriseOne 提供支援的企業單一登入 (SSO)。 如果您選取使用在 SSO**傳輸屬性**頁面上，認證會使用 SSO 認證資料庫中的分支機構應用程式。 分支機構應用程式代表需要認證的後端應用程式。  
  
### <a name="installed-components"></a>已安裝的元件  
* 配接器安裝會安裝並註冊下列元件在全域組件快取 (GAC) 中。 您可以確認註冊在檔案總管中開啟組件資料夾 (< %WINDIR%> \assembly)，或使用`gacutil /l`從 Visual Studio 命令提示字元：
  
    -   Microsoft.BizTalk.Adapters.BizUtil.dll    
    -   Microsoft.BizTalk.Adapters.JDEProperties.dll    
    -   Microsoft.BizTalk.Adapters.CoreManagement.dll    
    -   Microsoft.BizTalk.Adapters.CoreReceiver.dll    
    -   Microsoft.BizTalk.Adapters.CoreTransmitter.dll    

* 配接器專屬檔案會安裝在*Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\Bin*資料夾。 這個資料夾包含下列檔案：  
  
    -   Jdecba.dll    
    -   Microsoft.BizTalk.Adapters.JDEProperties.dll  
  
* 下列檔案會安裝在*Program Files\Microsoft BizTalk Adapters for Enterprise applications\j.d.edwards。Edwards EnterpriseOne(r)*:  
  
    -   Bin\BTAJDEEnterpriseOneTrace.cmd    
    -   Classes\JDEDynAccess.jar    
    -   Config\btaJDEEnterpriseOneTrace.mof    
    -   Config\jdearglist.txt    
    -   Config\jdeinterop.ini    
    -   Config\jdelog.properties    
    -   sdk  
  
 
## <a name="post-install---peoplesoft-enterprise"></a>後續安裝-PeopleSoft Enterprise  
 Microsoft BizTalk Adapter for PeopleSoft Enterprise 包含傳輸配接器，可將支援的資料庫和伺服器系統連接到 BizTalk Server。 傳輸配接器可讓您叫用從 BizTalk Server 的伺服器系統的呼叫。 傳輸配接器 (BizTalk Server 管理傳送處理常式) 組態會指定 SQL 資料庫的位置。  
  
 BizTalk Adapter for PeopleSoft Enterprise 提供支援的企業單一登入 (SSO)。 如果您選取使用在 SSO**傳輸屬性**頁面上，認證會使用 SSO 認證資料庫中的分支機構應用程式。 分支機構應用程式代表需要認證的後端應用程式。  
  
 配接器安裝包含 \sdk 目錄中的範例。  
  
### <a name="installed-components"></a>已安裝的元件  
* 配接器安裝會安裝並註冊下列元件在全域組件快取 (GAC) 中。 您可以確認註冊在檔案總管中開啟組件資料夾 (< %WINDIR%> \assembly)，或使用`gacutil /l`從 Visual Studio 命令提示字元：
  
    -   Microsoft.BizTalk.Adapters.BizUtil.dll    
    -   Microsoft.BizTalk.Adapters.CoreManagement.dll    
    -   Microsoft.BizTalk.Adapters.CoreReceiver.dll    
    -   Microsoft.BizTalk.Adapters.CoreTransmitter.dll    

* 配接器特定的檔案會安裝在*Program Files*和*Program Files\Common Files*。 下列檔案會安裝在*Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise (r)*:
  
    -   bin\BTAPeopleSoftTrace.cmd    
    -   config\btaPeopleSoftTrace.mof    
    -   config\GET_CI_INFO.pc    
    -   config\GET_CI_INFO.pc    
    -   sdk\<sdk  
  
* *程式 Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications*包含下列檔案：  
  
    -   bin\psosa.dll    
    -   bin\Microsoft.BizTalk.Adapters.CoreManagement.dll    
    -   bin\Microsoft.BizTalk.Adapters.CoreReceiver.dll    
    -   bin\Microsoft.BizTalk.Adapters.CoreTransmitter.dll  
  
## <a name="post-install-overview---tibco-rendezvous"></a>後續安裝概觀-TIBCO Rendezvous  
 Microsoft BizTalk Adapter for TIBCO Rendezvous 包含接收和傳輸功能，可支援的資料庫和 BizTalk server 的伺服器系統。  
  
-   接收端會接聽來自伺服器系統的輸出呼叫。  
  
-   傳輸端可讓您從 BizTalk Server 叫用伺服器系統的呼叫。  
  
 請參閱有關如何使用 Microsoft BizTalk Adapter for TIBCO Rendezvous 以及其模型與 BizTalk Server 模型之間的對應資訊的配接器文件。  
  
### <a name="installed-components"></a>已安裝的元件  
* 配接器安裝會安裝並註冊下列元件在全域組件快取 (GAC) 中。 您可以確認註冊在檔案總管中開啟組件資料夾 (< %WINDIR%> \assembly)，或使用`gacutil /l`從 Visual Studio 命令提示字元： 
  
    -   Microsoft.BizTalk.Adapters.TibcoRV    
    -   Microsoft.BizTalk.Adapters.TibcoRV.Common    
    -   Microsoft.BizTalk.Adapters.TibcoRV.Service    
    -   Microsoft.BizTalk.Adapters.TibRV.Properties    
    -   Microsoft.BizTalk.Adapters.TibcoEMS    
    -   Microsoft.BizTalk.Adapters.TibcoEMS.Properties    
    -   Microsoft.BizTalk.Adapters.TibcoRVManagement    
    -   Microsoft.BizTalk.Adapters.TibcoRVReceiver  
    -   Microsoft.BizTalk.Adapters.TibcoRVTransmitter  
  
* 配接器特定的檔案會安裝在*程式檔案和 Program Files\Common Files*。 下列檔案會安裝在*Program Files\Microsoft BizTalk Adapters for Enterprise Applications\ TIBCO(r) 器*:  
  
    -   bin\BTATibcoRVTrace.cmd    
    -   bin\mbaRV.exe    
    -   bin\Microsoft.BizTalk.Adapters.TibcoRV.Common.dll    
    -   bin\Microsoft.BizTalk.Adapters.TibcoRV.dll    
    -   bin\Microsoft.BizTalk.Adapters.TibcoRV.Service.dll    
    -   bin\Microsoft.BizTalk.Adapters.BizUtil.dll    
    -   bin\Microsoft.BizTalk.Adapters.CoreManagement.dll    
    -   bin\Microsoft.BizTalk.Adapters.CoreReceiver.dll    
    -   bin\Microsoft.BizTalk.Adapters.CoreTransmitter.dll    
    -   bin\Microsoft.BizTalk.Adapters.TibRV.Properties.dll    
    -   Config\btaTibcoRVTrace.mof    
    -   sdk\<sdk  
  
* *程式 Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications*包含下列檔案：  
  
    -   bin\tibcorvcba.dll    
    -   Microsoft.BizTalk.Adapters.CoreManagement.dll    
    -   Microsoft.BizTalk.Adapters.CoreReceiver.dll    
    -   Microsoft.BizTalk.Adapters.CoreTransmitter.dll  
  
### <a name="add-tibcorendezvousdll-to-the-gac"></a>將 TIBCO。Rendezvous.dll gac  
 BizTalk Adapter for TIBCO Rendezvous 需要**TIBCO。Rendezvous.dll**檔案。 所需的最低版本是 1.0.3036.23330 FileVersion，隨附於產品 8.1 版。 配接器會觸發例外狀況，並記錄適當的訊息，如果未安裝這個組件。  
  
 若要載入的組件，讓 TIBCO 的特定版本時，TIBCO Rendezvous 組件不會失敗，您必須使用晚期繫結。Rendezvous.dll 和 TIBCO。Rendezvous.net 模組不在目標電腦上。
  
 **執行階段元件**  
  
 確認您的電腦上已安裝 TIBCO Rendezvous 執行階段元件。 執行階段元件是安裝 TIBCO Rendezvous 時唯一必須安裝的元件。  

1. 在 Visual Studio 命令提示字元中，將目錄變更至 TIBCO 的位置。Rendezvous.dll 檔案。 TIBCO Rendezvous 的預設安裝中，這個 DLL 的路徑是**C:\TIBCO\TIBRV\BIN\TIBCO。Rendezvous.dll**。  
  
2. 在命令提示字元中，請輸入下列項目：  
  
```
C:\TIBCO\TIBRV\BIN > gacutil /i TIBCO.Rendezvous.dll
```
  
 TIBCO.Rendezvous.dll 現在會顯示 GAC 清單。 若要檢視清單中，控制台 中，開啟**系統管理工具**，開啟**Microsoft.NET Framework 組態**，然後開啟**組件快取**。  
  
## <a name="post-install---tibco-enterprise-message-service"></a>後續安裝-TIBCO Enterprise Message Service  
 Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) 包含接收和傳輸功能，可將支援的資料庫和伺服器系統連接到 BizTalk Server。  
  
-   接收端會接聽來自伺服器系統的輸出呼叫。  

-   傳輸端可讓您從 BizTalk Server 叫用伺服器系統的呼叫。  
  
 請參閱有關如何使用 BizTalk Adapter for TIBCO EMS 以及其模型與 BizTalk Server 模型之間的對應資訊的配接器文件。  
  
### <a name="installed-components"></a>已安裝的元件  
* 配接器安裝會安裝並註冊`Microsoft.BizTalk.Adapters.TibcoEMS.dll`在全域組件快取 (GAC) 中的檔案。 您可以確認註冊在檔案總管中開啟組件資料夾 (< %WINDIR%> \assembly)，或使用`gacutil /l`從 Visual Studio 命令提示字元。
  
* 配接器特定的檔案會安裝在*Program Files*和*Program Files\Common Files*。 下列檔案安裝下*Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) 企業訊息 Service(TM)*:  
  
    -   bin\BTATibcoEMSTrace.cmd    
    -   Microsoft.BizTalk.Adapters.TibcoEMS.dll    
    -   Config\btaTibcoEMSTrace.mof    
    -   sdk\<sdk  
  
* *程式 Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin*資料夾包含下列檔案：  
  
    -   Microsoft.BizTalk.Adapters.CoreManagement.dll    
    -   Microsoft.BizTalk.Adapters.CoreReceiver.dll    
    -   Microsoft.BizTalk.Adapters.CoreTransmitter.dll  
  
    > [!NOTE]
    >  您必須使用晚期繫結來載入組件，如此一來，當目標電腦上沒有特定版本的 TIBCO.EMS.dll 時，TIBCO EMS 組件才不會失敗。  
  
### <a name="add-tibcoemsdll-api-to-the-gac"></a>將 TIBCO。EMS.dll API 加入 GAC  
 BizTalk Adapter for TIBCO EMS 會要求您將 TIBCO.EMS.dll 加入 GAC。 如果未安裝這個組件，BizTalk Adapter for TIBCO EMS 會觸發例外狀況並記錄適當的訊息。  
  
1.  將 TIBCO EMS C#API 複製到您的 BizTalk 電腦。  
  
2.  在 Visual Studio 命令提示字元中，將目錄變更到 C# API 檔案的位置。  
  
3.  在 Visual Studio 命令提示字元中輸入下列命令：  
  
    ```
    C:\\<TIBCO EMS Folder\>bin> gacutil /i TIBCO.EMS.dll
    ```
  
 TIBCO.EMS.dll 現在會顯示在 C:\Windows\assembly 清單中。 或者，在控制台中開啟**系統管理工具**，開啟**Microsoft.NET Framework**，並開啟**組件快取**若要檢視 GAC 清單。  
  
 **限制**  
  
 BizTalk Adapter for TIBCO EMS 使用 TIBCO.EMS.dll 與伺服器通訊。 以下是使用 TIBCO.EMS.dll 的限制：  
  
1.  無法使用訊息壓縮功能，該功能可讓 TIBCO EMS 用戶端將壓縮格式的訊息傳送給 EMS。  
  
2.  無法加密配接器和伺服器之間的訊息。 TIBCO.EMS.dll 不允許使用 OpenSSL 程式庫進行 SSL 加密，但配接器支援使用 Tibco.EMS.dll 搭配 ProductVersion 5.0 及更新版本的 SLL。  
  
3.  不支援 EMS 的系統管理 API。  
  
## <a name="adapter-tracing"></a>配接器追蹤

### <a name="enable-tracing"></a>啟用追蹤
 系統管理員可決定要使用 Windows 追蹤的檔案名稱。 這個應用程式會寫入至作業系統，並在您需要特定後端系統的記錄檔之前，略過所有記錄檔。 您可以執行個別適用於企業應用程式的 BizTalk Adapter 命令檔，來執行這項作業。 該命令的引數的其中一個是用來擷取追蹤資訊的檔案名稱。 如需詳細資訊，請參閱 「 使用 Windows 追蹤事件 」 （在本主題中）。
  
 追蹤檔案將安裝至 * \Program Files\Microsoft BizTalk Adapters for Enterprise Applications\*。  
  
-   bin\BTATrace.cmd    
-   config\btaTrace.mof  
  
### <a name="use-windows-trace-event"></a>使用 Windows 追蹤事件  
 配接器會將錯誤、警告和資訊訊息記錄至 Windows 事件檢視器。 您可以使用 Windows 事件追蹤 (ETW) 工具來檢視其他追蹤訊息。 當 ETW 啟用時，它會建立 *.etl 檔案以接收訊息。 這個檔案是二進位格式，必須經過轉換才能讀取。 若要這樣做，您必須取用者應用程式可供解譯\*.etl 檔案，例如 Windows tracerpt.exe 或 tracedmp.exe。  
  
### <a name="etw-components"></a>ETW 元件
  
 「Windows 事件追蹤」有三個元件：  
  
* **控制器應用程式：**啟動與停用提供者。 例如，tracelog.exe 或 logman.exe。  
  
    您會將 PATH 環境變數設定成指向 tracelog.exe 的位置。 這可確保該 BTA < 配接器名稱\>追蹤呼叫可在系統中找到 tracelog.exe。 根據預設，BTA < 配接器名稱\>追蹤搜尋目前的路徑。  
  
    > [!NOTE]
    >  tracelog.exe 可以從 Microsoft SDK，並提供 Microsoft BizTalk Adapters for Enterprise Applications 的命令相容。 如果要使用 logman.exe，請參閱 logman 文件。  
  
* **取用者應用程式：**讀取記錄的事件。  
  
    如果要讓取用者應用程式可讀取 .etl 檔案中的事件，「Windows 事件追蹤」必須將它們傾印到該檔案。 此動作通常是在控制器停用追蹤後完成的。  
  
    若要使用取用者應用程式，而不停用追蹤，控制器必須啟動使用即時選項時，追蹤**< 即時\>=-rt**。  
  
* **提供者：**用來提供事件。  
  
    每個配接器包含五個不同的提供者。 它們是在 Windows Management Instrumentation (WMI) 中註冊的。 若要在 root\WMI\EventTrace 路經中尋找已登錄的提供者，您可以使用諸如 WMI CIM Studio 這類的工具。  
  
    這五個提供者可讓您記錄不同的訊息類型：  
  
        -   **Receiver Logging Provider**: The <Trace element\> switch is - **receiver**.    
        -   **Receiver CastDetails Provider**: The <Trace element\> switch is - **castDetailsReceive**.    
        -   **Transmitter Logging Provider**: The <Trace element\> switch is - **transmitter**.    
        -   **Transmitter CastDetails Provider**: The <Trace element\> switch is - **castDetailsTransmit**.    
        -   **Management Logging Provider**: The <Trace element\> switch is - **management**.  
  
若要使用 ETW，執行特定的配接器的命令： `BTA<Adapter Name\>Trace.cmd`。 您可以下列方式使用此命令：  
  
```  
BTA<Adapter Name>Trace <Trace element> -start [-cir <MB>|   
    -seq <MB>] [-rt] logfile  
BTA<Adapter Name>Trace <Trace element> -stop  
  
```  
  
 其中：  
  
**< 追蹤項目\>** （必要） 是提供者的類型。 選項包括：  
  
 **-castDetailsTransmit**  
  
 **-傳輸器**  
  
 **-castDetailsReceive**  
  
 **-接收者**  
  
 **-管理**  
  
 **-開始、-停止：**啟用或停用提供者。  
  
 **-cir < MB\>:**檔案的大小與種類。 **-cir**是循環檔案。 **< MB\>:**大小以 mb 為單位。  
  
 **-seq < MB\>:**檔案的大小與種類。 **-seq**是循序檔案。 **< MB\>:**大小以 mb 為單位。  
  
 **-rt:**上設定的即時模式。  
  
 **記錄檔：**記錄檔的名稱 （c:\rtlog.etl 是預設值）。  
  
 例如：  
  
```  
BTAXXXTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTAXXXTrace -transmitter -stop  
  
```  
  
> [!NOTE]
>  您可以使用 tracerpt.exe 命令來格式化 .etl 檔案。  

## <a name="next-steps"></a>後續的步驟
* [JD Edwards EnterpriseOne 配接器](../core/jd-edwards-enterpriseone-adapter.md)
* [JD Edwards OneWorld 配接器](../core/jd-edwards-oneworld-adapter.md)
* [PeopleSoft Enterprise 配接器](../core/peoplesoft-enterprise-adapter.md)
* [TIBCO Enterprise Message Service 配接器](../core/tibco-enterprise-message-service-adapter.md)
* [TIBCO Rendezvous 配接器](../core/tibco-rendezvous-adapter.md)
