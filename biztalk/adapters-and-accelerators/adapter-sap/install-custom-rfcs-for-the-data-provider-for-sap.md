---
title: 安裝適用於 SAP 的資料提供者的自訂 Rfc |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installation, custom RFCs for the Data Provider for SAP
- installing, custom RFCs for the Data Provider for SAP
- installing custom RFCs, how to
ms.assetid: 7a99db70-fa5a-4c04-9dc7-b71613d4364e
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 648a1780e02e35d284a620f29cfd034765c4cc45
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752766"
---
# <a name="install-custom-rfcs-for-the-data-provider-for-sap"></a>安裝適用於 SAP 的資料提供者的自訂 Rfc
如果您想要使用.NET Framework Data Provider for mySAP Business Suite 存取 SAP 系統，請安裝自訂的 Rfc。

[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]需要自訂 Rfc 來執行 SAP 系統的某些作業：
  
- 執行選取的作業，[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]需要 Z_EXTRACT_DATA_OO RFC。  
  
- 執行 EXECQUERY 作業，[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]需要 Z_EXECUTE_SAP_QUERY RFC。  
  
若要執行這些 SAP 系統上的作業，您必須安裝這些自訂 Rfc，SAP 系統上。 如果您選擇要安裝[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]連同[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，安裝程式複製的 RFC 傳輸[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]的壓縮檔 (customRFC.zip) 系統上安裝配接器的位置。 Zip 檔案通常會安裝在*\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Microsoft.NET Framework Data Provider for mySAP Business Suite*。 
  
 Zip 檔案解壓縮之後，您會發現四個資料檔案，兩個遵循命名模式 K9\*。BI1 （例如，類似於 K900534。BI1) 和其他兩個模式 R9\*。BI1 （例如，類似於 R900534。BI1)。  
  

  
1. 已解壓縮的檔案複製到 SAP 應用程式伺服器執行的配接器的電腦。  
  
   1.  SAP 應用程式伺服器，您的開發系統的 SAP R/3 系統管理員身分登入。  
  
   2.  複製兩個傳輸檔案的命名模式 K9\*。從 SAP 應用程式伺服器上執行到下列目錄的介面卡的電腦上安裝目錄 BI1:  
  
        `<drive>:\usr\sap\trans\cofiles`  
  
   3.  複製兩個傳輸檔案的命名模式 R9\*。從 SAP 應用程式伺服器上執行到下列目錄的介面卡的電腦上安裝目錄 BI1:  
  
        `<drive>:\usr\sap\trans\data`  
  
2. 載入的 SAP 應用程式伺服器上的傳輸緩衝區的傳輸。  
  
   1.  在命令提示字元中，瀏覽至 SAP 應用程式伺服器上的傳輸程式目錄：  
  
        `<drive>:\usr\sap\trans\bin`  
  
   2.  若要載入的傳輸緩衝區的傳輸，執行下列命令，`\usr\sap\trans\bin`目錄和取代*sysid*與您的開發系統的系統識別碼：  
  
       ```  
       tp addtobuffer <TransportNumber> <sysid> pf=TP_DOMAIN_<sysid>.PFL  
       ```  
  
        其中， *TransportNumber*是實際傳輸數字 (例如 BI1K900534)。  
  
   3.  之後`tp`命令完成時，您會看到類似下列報表：  
  
       ```  
       This is tp version 320.56.66 (release 620)  
       Addtobuffer successful for TransportNumber  
       tp finished with return code: 0  
       ```  
  
        傳回碼為"0"表示作業成功。  
  
        傳回碼為 0 或 4 是可接受的。 如果您收到的 8 個以上的傳回碼，請連絡 Microsoft 客戶服務及支援。  
  
       > [!IMPORTANT]
       >  傳輸檔案的第二個集合，請重複步驟 (b) 和 (c)。  
  
       > [!NOTE]
       >  輕鬆地，您就可以從 cofile 檔案名稱衍生實際傳輸數目。 例如，名為 K900534 cofile。BI1 提供 BI1K900534 傳輸數目。  
  
3. 匯入 SAP 傳輸。  
  
   1.  執行下列命令在命令提示字元：  
  
       ```  
       tp import <TransportNumber> <sysid> client=<clientnumber> pf=TP_DOMAIN_<sysid>.PFL  
       ```  
  
        取代*sysid*與您的開發系統的系統識別碼。 取代*clientnumber*與您的開發系統的用戶端編號。  
  
        您可以使用 U2 參數來覆寫先前安裝的物件，如下所示：  
  
       ```  
       tp import <TransportNumber> <sysid> client=<clientnumber> U2  
       ```  
  
        中的多個  
  
       ```  
       tp import <TransportNumber> <sysid> client=<clientnumber> pf=TP_DOMAIN_<sysid>.PFL U2  
       ```  
  
       > [!NOTE]
       >  輕鬆地，您就可以從 cofile 檔案名稱衍生實際傳輸數目。 例如，名為 K900534 cofile。BI1 提供 BI1K900534 傳輸數目。  
  
   2.  之後`tp`命令完成時，您會看到類似下列報表：  
  
       ```  
       This is tp version 320.56.66 (release 620)  
       This is R3trans.exe version 6.08 (release 620 - 04.02.03 - 14:54:00).  
       R3trans.exe finished (0000).  
       This is R3trans.exe version 6.08 (release 620 - 04.02.03 - 14:54:00).  
       R3trans.exe finished (0000).  
       tp finished with return code: 0  
       ```  
  
        傳回碼為"0"表示作業成功。  
  
        傳回碼為 0 或 4 是可接受的。 如果您收到的 8 個以上的傳回碼，請連絡 Microsoft 客戶服務及支援。  
  
       > [!IMPORTANT]
       >  第二組傳輸檔案，請重複步驟 （a） 和 (b)。  
  
4. 檢查傳輸記錄檔。  
  
5. 檢查 SAP GUI 傳輸使用交易 SE09 以確認沒有任何錯誤的組合管理 中的傳輸記錄檔。  
  
   設定使用者的授權  
   Z_EXTRACT_DATA_OO RFC 需要具有特定授權物件的使用者識別碼。 使用 SAP GUI 授權系統管理工具的 RFC 執行上設定的最小的限制：  
  
> [!NOTE]
>  您不需要設定 Z_EXECUTE_SAP_QUERY RFC 的授權。  
  
- Z_EXTRACT_DATA_OO 需要 S_TABU_DIS 和 Z_EIP_TABL。 下列的值提供 S_TABU_DIS，允許使用者檢視系統中的任何資料表的中繼資料的最小限制。  
  
  - ACTVT: 03  
  
  - DICBERCLS: \*  
  
    您可以使用 DICBERCLS 授權類別所限制資料表的授權。  
  
    若要檢視資料表的授權類別，您可以使用 TDDAT 資料表。  
  
  > [!NOTE]
  >  若要防止資料表維護交易資料表的變更，您應該只授與在生產環境中的顯示權限 (ACTVT: 03 設定允許的活動，以顯示)。  
  
   Z_EIP_TABL 最小值為：  
  
  - ACTVT: 03  
  
  - 資料表： \*  
  
    您可以使用資料表來明確定義授權的資料表。 也請注意，S_TABU_DIS 也用於其他交易。  
  
##### <a name="to-set-user-authorization"></a>若要設定使用者的授權  
  
1.  啟動 SAP GUI。 移至 T-程式碼類型`pfcg`，然後按 ENTER。  
  
2.  在 **角色**文字中，輸入您想要建立此項目，例如，角色名稱`ZTEST`，然後按一下 **角色**。  
  
3.  在 [ **Create Role**頁面上，按一下**授權**] 索引標籤。  
  
     如果出現提示，儲存角色，請按一下**是**。  
  
4.  在 [**變更角色**頁面上，按一下**變更授權資料**] 按鈕。  
  
5.  如果系統提示您選取的範本**選擇範本** 對話方塊中，按一下**請勿選取範本**。  
  
6.  在 [**變更角色： 授權**頁面上，按一下**手動**] 按鈕。  
  
7.  在 **手動選取的授權**方塊中，輸入授權物件的名稱`Z_EIP_TABL`按 ENTER 鍵。  
  
8.  在 **變更角色： 授權**頁面上，展開節點，直到您看到的文字方塊**活動**並**資料表名稱**。 針對**活動**文字方塊中，輸入值`03`。 針對**資料表名稱**文字方塊中，輸入值`*`。  
  
9. 按一下 **儲存**按鈕，以產生設定檔。  
  
10. 請返回**變更角色**頁面，然後按一下**使用者** 索引標籤。  
  
11. 在 **使用者**索引標籤上，輸入使用者名稱中的指派角色的使用者識別碼**使用者識別碼**資料行，然後按一下 **使用者比較** 按鈕。  
  
12. 在 **比較角色使用者的主要記錄**，按一下**完成比較**更新主要資料錄。 出現提示時，儲存角色，按一下**是**。  
  
13. 儲存並結束。  
  
確認自訂 RFC 的安裝  
 安裝自訂的 Rfc 之後，您可以確認 Rfc 是否已正確安裝。  
  
- Z_EXECUTE_SAP_QUERY RFC，您可以執行這項作業執行的預先定義的查詢中 SAP 系統使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。  
  
- Z_EXTRACT_DATA_OO RFC，您可以執行這項作業執行下列測試，確認 RFC 運作，並在您的系統可供使用。  
  
##### <a name="to-test-the-installation-of-zextractdataoo"></a>若要測試的 Z_EXTRACT_DATA_OO 安裝  
  
1.  在 SAP GUI 授權系統管理工具中，執行 SE37，函式模組 Z_EXTRACT_DATA_OO，，然後在按下的測試模式中執行 RFC `F8`。 會填入參數，如下所示。  
  
    |||  
    |-|-|  
    |IN_METADATA_ONLY||  
    |IN_METADATA_LANGUAGE|EN|  
    |IN_FROM_TABLE|T000|  
    |IN_OUTPUT_MODE|S|  
    |IN_OUTPUT_FILENAME||  
    |IN_USE_FIELD_EXITS|X|  
    |IN_SET_ROWCOUNT|0|  
    |IN_DELIMITER||  
    |IN_PACKET_SIZE|50,000|  
    |IN_MAX_WRITE_ATTEMPTS|4|  
    |IN_RETRY_DELAY|30|  
    |IN_SQL_DATES_ON||  
  
2.  按一下  **Execute**或按`F8`。  
  
3.  在 [結果] 窗格中，請檢查下列項目。  
  
    |||  
    |-|-|  
    |OUT_TABLEHEADER|\<T000 一般的中繼資料\>|  
    |OUT_TECHNICALSETTINGS|\<T000 技術的資料庫層級的中繼資料\>|  
    |OUT_RECORDLENGTH|\<取決於 SAP 版本\>|  
    |OUT_RECORDCOUNT|\<在您的系統上 T000 SE16 確認用戶端數目\>|  
    |OUT_ZDATATABLE|\<確認這個結果與使用 SE 16 T000 上的資料來源\>|  
    |OUT_RETURN_TAB|S 001 成功|  
  
## <a name="remove-the-rfc-for-the-data-provider-for-sap"></a>移除適用於 SAP 的資料提供者的 RFC  
  
1.  在 SAP GUI 物件導覽 (SE80)，尋找與 ZMSBI 開發類別的所有物件。  
  
2.  從下列的字典物件資料夾中刪除與 ZMSBI 開發類別的所有物件：  
  
    -   結構  
  
    -   函式群組  
  
    -   已獲授權的物件  
  
3.  引發的傳輸，並將它移轉透過每個系統的 RFC （開發、 測試和生產系統，例如） 的安裝位置。  
  
     如需進一步協助，請連絡您的 SAP 基礎系統管理員。  
     
## <a name="next"></a>下一個
[了解 BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)  
[SAP 配接器教學課程](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)