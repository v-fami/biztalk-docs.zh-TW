---
title: 搭配使用 SharePoint 與 Oracle 資料庫配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 254204e5-3b5d-4e70-97ab-817660d1206a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa6e5f92bcb1ddd579b70912b98fc0f08165bca6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975375"
---
# <a name="use-the-oracle-database-adapter-with-sharepoint"></a>搭配使用 SharePoint 與 Oracle 資料庫配接器
WCF 配接器服務開發精靈 」，如[!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]可以讓 Microsoft BizTalk Adapter for Oracle 資料庫和 Microsoft BizTalk Adapter for Oracle E-business Suite 直接與 Microsoft sharepoint 的外部資料來源使用。 啟動 新增服務開發精靈支援這項功能卻**WCF 配接器服務**來建立新 Visual C# 中的網站範本[!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]。 範本會包含[!INCLUDE[adapterpacknoversion_md](../../includes/adapterpacknoversion-md.md)]。 您也必須安裝 Microsoft Windows Communication Foundation (WCF) 的企業營運 (LOB) 配接器 SDK。  
  
## <a name="sharepoint-operation-support"></a>SharePoint 作業的支援  
 配接器服務開發精靈產生的 Oracle 配接器的特殊服務合約，適用於 Microsoft SharePoint。 精靈會產生服務合約，其中包含與 Microsoft SharePoint 整合配接器執行下列作業：  
  
- **建立：** CreateItem_ 作業支援。  
  
- **讀取：** ReadItem_ 作業支援。  
  
- **更新：** UpdateItem_ 作業支援。  
  
- **刪除：** DeleteItem_ 作業支援。  
  
- **查詢：** ReadList 作業支援。  
  
- **建立關聯：** Associate_ 作業支援。  
  
  下列服務合約產生使用 Microsoft BizTalk adapter for Oracle Database 做為範例。 配接器設定為提供存取權的 EMP 資料表  
  
```  
    [System.ServiceModel.ServiceContractAttribute()]  
    public interface ISCOTT_EMP {  
  
    [System.ServiceModel.OperationContractAttribute()]  
    SCOTT_EMP_Record[] ReadList(System.Nullable<int> Limit);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    void CreateItem(SCOTT_EMP_Record Input);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    SCOTT_EMP_Record[] ReadItem_EMPNO(System.Nullable<decimal> EMPNO);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    void UpdateItem_EMPNO(SCOTT_EMP_Record Input);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    void DeleteItem_EMPNO(System.Nullable<decimal> EMPNO);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    SCOTT_EMP_Record[] Associate_DEPTNO(System.Nullable<decimal> DEPTNO);  
}  
```  
  
## <a name="create-a-new-web-site-to-host-the-oracle-database-in-iis"></a>建立新的網站裝載在 IIS 中的 Oracle 資料庫  
 下列步驟提供使用 WCF 配接器服務開發精靈來建立新的 WCF web 服務，裝載 Microsoft BizTalk Adapter for Oracle Database 的範例。 服務合約會包含與 Sharepoint 直接相容的作業。 因此，它可以直接作為外部資料來源。 配接器設定為使用 Oracle 資料庫驗證**SCOTT**帳戶。 如果**SCOTT**帳戶已被鎖定，您可以藉由以 sysdba 身分的登入 SQL Plus 解除鎖定帳戶。  
  
```  
<Oracle Installation Bin Directory>\Sqlplus.exe SYS AS SYSDBA  
```  
  
 然後執行下列命令。  
  
```  
SQL> ALTER USER scott ACCOUNT UNLOCK;  
```  
  
#### <a name="create-the-new-web-site-project"></a>建立新的網站專案  
  
1. 開啟 Visual Studio。   
  
2. 在 Visual Studio 中，在**檔案**功能表上，選取**新增**，然後按一下 **專案**。  
  
3. 在 **新的專案**對話方塊方塊中，展開**其他語言**，按一下  **Visual C#**。 尋找**WCF 配接器服務**在範本清單中，按一下以選取它。  
  
   > [!NOTE]
   >  **WCF 配接器服務**未提供範本如果[!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)]未安裝。 在 x64 上的系統，同時安裝 x86 和 x64 版本的[!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)]。  
  
4. 指定**ScottEMP**做為名稱，然後按一下**確定**。 **WCF 配接器服務開發精靈**啟動。  
  
5. 在 [**簡介**頁面上，按一下**下一步]**。  
  
6. 在 **選擇 Operations**頁面上，指定**oracleDBBinding**繫結。  
  
7. 按一下 [**設定**] 按鈕。 **設定配接器** 對話方塊隨即出現。  
  
8. 在 **安全性**索引標籤上，選取**Username**中**用戶端認證類型**下拉式清單方塊。  
  
9. 請輸入**SCOTT**使用者名稱，和 SCOTT 帳戶輸入正確的密碼。 SCOTT 帳戶的預設密碼**tiger**。  
  
10. 按一下 [ **URI 屬性**索引標籤上，輸入您的 Oracle 伺服器的 IP 位址或主機名稱**ServerAddress** ] 方塊中。  
  
11. 輸入正確 Oracle 資料庫中的服務執行個體名稱**ServiceName**  方塊中。 您可以從 「 Oracle Enterprise Manager 複製執行個體名稱資訊。  
  
12. 按下 **[確定]** 按鈕**設定配接器**對話方塊  
  
13. 上**選擇 Operations**頁面的精靈中，按一下**Connect**按鈕並等候幾分鐘才會針對 Oracle 資料庫來建置的類別。  
  
14. 類別中加入後**選取一個類別**清單中，向下捲動至**SCOTT**並將其展開。 然後展開**表格**然後按一下**EMP**表項目。  
  
15. 在 [**可用的類別和作業**清單，選取清單中的所有作業，然後按一下**新增**] 按鈕。 所有作業會都新增至**都新增的類別和作業**清單。  
  
16. 在 **選擇 Operations**頁面上，按一下**下一步**  按鈕。  
  
17. 在 **設定服務與端點行為**頁面上，將**UseServiceCertificate**服務行為加入**false**此範例中。 然後按一下**下一步**  按鈕。  
  
18. 在 [**設定服務端點繫結和位址**頁面上，按一下**套用**] 按鈕。 然後按一下**下一步**  按鈕。  
  
19. 在 [**摘要**頁面上，按一下**完成**] 按鈕。  
  
20. 按一下 [**建置**] 功能表選項，然後按**建置方案**。 請確認專案建置成功，出現任何錯誤。  
  
## <a name="publish-the-new-service-to-iis"></a>將新的服務發行至 IIS  
 此範例中您將發行到本機 IIS web 伺服器的配接器主機服務。  
  
1.  適用於 Visual Studio 方案總管 中以滑鼠右鍵按一下**ScottEmp**專案，然後按一下**屬性**。 專案設計工具索引標籤會顯示。  
  
2.  按一下  **Web**索引標籤，然後按一下**使用本機 IIS Web 伺服器**選項。  
  
3.  按一下 [**建立虛擬目錄**] 按鈕。  
  
4.  開啟網頁瀏覽器服務位址**http://localhost/ScottEmp/ISCOTT_EMP.svc**。 您應該會收到一則訊息指出 「 您已建立服務 」 表示配接器裝載在 IIS 中。  
  
## <a name="add-the-external-data-source-to-a-sharepoint-site-using-sharepoint-designer"></a>將外部資料來源新增至 SharePoint 網站，使用 SharePoint Designer  
 本節說明如何做為外部資料來源中加入新的網站上，使用 SharePoint Designer 的 WCF 服務。  
  
  
1.  開啟 SharePoint Designer，然後建立新的網站。  
  
2.  在 SharePoint Designer 中，依序展開**瀏覽**然後按一下**外部內容類型**中**站台物件**清單。  
  
3.  按一下 **外部內容類型**功能表按鈕，以建立新的外部內容類型。  
  
4.  按一下旁邊的文字**名稱**編輯新的外部內容類型的名稱。 請輸入**OracleEMP**的名稱。  
  
5.  按一下 [文字] 連結旁邊**外部系統**equivalence**探索外部的資料來源和作業，請按一下這裡。**。 這會開啟作業設計工具 OracleEMP 外部內容類型。  
  
6.  按一下 **加入連接**探索畫面上的按鈕。  
  
7.  在 外部資料來源類型選取項目 對話方塊中，選擇**WCF 服務**然後按一下**確定** 按鈕。  
  
8.  在 WCF 連接對話方塊中，在**服務中繼資料 URL**  方塊中輸入 **https://localhost/ScottEmp/ISCOTT_EMP.svc?wsdl**  
  
9. 在 [**服務端點 URL** ] 方塊中輸入 **https://localhost/ScottEmp/ISCOTT_EMP.svc**  
  
10. 按一下 **確定**按鈕可關閉 WCF 連接對話方塊。  
  
11. 一旦已填入資料來源資訊，依序展開**https://localhost/ScottEmp/ISCOTT_EMP.svc**資料來源，然後展開**Web 方法**。  
  
12. 以滑鼠右鍵按一下**ReadList** Web 方法，然後按一下**新讀取清單作業**。 [讀取列出組態] 對話方塊就會啟動。  
  
13. 在讀取清單對話方塊中按一下**傳回的參數**然後按一下**EMPNO**在資料來源項目。 按一下 **對應至識別碼**。  
  
14. 按一下 [**完成**在讀取清單] 對話方塊中的色彩。  
  
15. 輸入儲存新的外部資料來源**Ctrl + s**。  
  
#### <a name="test-the-external-data-source-connection"></a>測試外部資料來源連接  
  
1.  在新的網站上，按一下**建立清單和表單** 按鈕。 建立清單和表單 OracleEMP 對話方塊隨即出現。  
  
2.  請輸入**OracleEMP_List**的清單名稱，然後按一下**確定** 按鈕。  
  
3.  一旦已建立清單，請按一下**摘要檢視**功能表上的按鈕。  
  
4.  按一下  **OracleEMP_List**下外部清單。  
  
5.  按一下 **在瀏覽器中的預覽**測試配接器的 ReadList 操作功能表上的按鈕。  
  
## <a name="troubleshoot"></a>疑難排解
  
-   64 位元電腦上您必須確定也會安裝 32 位元 Oracle 用戶端元件。 這是因為 Visual Studio 和它的精靈會執行以 32 位元處理序在開發期間需要 32 位元元件的存取權。