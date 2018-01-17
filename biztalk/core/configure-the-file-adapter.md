---
title: "設定 File 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- File adapters, configuring
- configuring [File adapters], about configuring File adapters
- configuring [File adapters]
ms.assetid: 1e0c7e20-80f8-469b-b423-34a2b90f9ec3
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2f2de6a4c4cae93db90f0fb2cfc79321bfc7b3e
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="configure-the-file-adapter"></a>設定 File 配接器
如何設定 File 配接器、 讀取的安全性建議，並檢視所需的權限。

您可以建立接收位置和傳送埠使用 [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], ，或以程式設計的方式。 本主題著重於 [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] 主控台。 如需以程式設計方式的步驟，請移至[建立接收位置或傳送埠，以程式設計方式](../core/create-the-receive-location-and-send-port-programmatically.md)。

> [!IMPORTANT]
> **從開始 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, ，您可以連接至 Azure 檔案共用使用 File 配接器。 Azure 儲存體帳戶必須在 BizTalk Server 上裝載。 [開始使用 Azure 檔案儲存體，在 Windows 上](https://docs.microsoft.com/azure/storage/storage-dotnet-how-to-use-files#mount-the-file-share) 列出掛接步驟。

## <a name="security-recommendations"></a>安全性建議

FILE 配接器負責在 BizTalk Server 的某個目錄中傳輸檔案。 建議您依照這些指導方針，來保護和部署您作業環境中的 FILE 配接器。  
  
-   不會開啟連接埠可連接至周邊網路中的檔案共用。 您應該在具有高度信任的環境中使用 FILE 配接器，例如內部網路。 
  
-   在接收位置的放置目錄設定強式判別存取控制清單 (DACL)。 例如，您必須對檔案接收位置收取訊息的目錄設定讀取、寫入、刪除檔案及刪除子資料夾與檔案的權限，使得只有授權的使用者可以在此位置中放置訊息。  
  
-   當您使用 FILE 配接器收取重要資料時，建議您使用「網際網路通訊協定安全性」(IPSec)。  
  
## <a name="required-permissions"></a>必要權限

選取配接器處理常式的主控件執行個體的安全性內容下，執行配接器處理常式。 主控件執行個體使用 `Logon` 屬性 ***主機名稱* -主控件執行個體屬性** 在 BizTalk 管理。 這 `Logon` 帳戶必須具有任何資料夾或共用檔案配接器使用的特定權限。

處理常式所使用主控件執行個體的使用者帳戶需要下列權限。 ✔ 表示需要的權限。 空白項目表示不需要權限。

| Permissions | 接收處理常式 | 傳送處理常式 |
| --- | --- | --- |
| 完整控制 | ✔ <br/> 共用層級 （若存取檔案共用） |  | 
| 周遊資料夾 / 執行檔案 |  | ✔ <br/> 在檔案層級 | 
| 列出資料夾/讀取資料 | ✔ <br/> 在檔案層級 | ✔ <br/> 在檔案層級 | 
| 讀取屬性 | | ✔ <br/> 在檔案層級 | 
| 讀取擴充屬性 | | ✔ <br/> 在檔案層級 | 
| 建立檔案 / 寫入資料 | | ✔ <br/> 在檔案層級 | 
| 建立資料夾 / 附加資料 | | ✔ <br/> 在檔案層級 | 
| 刪除子資料夾及檔案 | ✔ <br/> 在檔案層級 | ✔ <br/> 在檔案層級 | 
| 讀取權限 | | ✔ <br/> 在檔案層級 | 
| 變更 | | ✔ <br/> 共用層級 （若存取檔案共用） |

> [!TIP] 
> 在檔案層級中，開啟 **進階權限** 檔案或資料夾，以查看這些權限。

> [!NOTE] 
> 每個主控件只可和一個接收處理常式建立關聯。  

## <a name="configure-the-receive-location"></a>設定接收位置
  
> [!NOTE]
>  之前完成下列程序，您必須已經新增單向接收埠。 請參閱 [如何建立接收埠](../core/how-to-create-a-receive-port.md)。  
  
1.  在 BizTalk Server 管理主控台中，依序展開 [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 **[BizTalk 群組]**、 **[應用程式]**，以及您要在其下建立接收位置的應用程式。  
  
2.  在左窗格中，按一下  **接收埠** 節點。 然後在右窗格中，使用滑鼠右鍵按一下與現有接收位置關聯的接收埠，或是您要與新接收位置關聯的接收埠，然後按一下 **[屬性]**。  
  
3.  在左窗格中 **接收埠屬性** 對話方塊中，選取 **接收位置**, ，並在右窗格按兩下現有接收位置或按一下 **新增** 來建立新的接收位置。  
  
4.  在 **接收位置屬性** 對話方塊中，於 **傳輸** 區段中，選取 **檔案** 從下拉式清單中，輸入，然後按一下 **設定** 設定接收位置的傳輸屬性。  
  
5.  在 **一般** 索引標籤上，執行下列動作︰  
  
    |使用|動作|  
    |--------------|----------------|  
    |**接收資料夾**|必要。 輸入資料夾的路徑上檔案系統、 網路共用，或在檔案接收處理常式的 Azure 檔案共用讀取檔案。 您可以輸入路徑直接在 **接收資料夾** 文字 方塊中，也可以從檔案系統使用 **瀏覽**  按鈕。 當瀏覽資料夾，您也可以建立新資料夾，請使用 **建立新資料夾**。<br /><br /> 如果使用 Azure 檔案儲存體共用，請輸入 `\\yourfilestoragename.file.core.windows.net\yourfilesharename`。 <br /><br />**類型︰** 字串 <br/><br/>**注意︰**  不要設定 **接收資料夾** 屬性設為使用含有符號連結的 「 NT 分散式檔案系統資料夾。 如果您使用 NT 分散式檔案系統，您只能使用資料夾含有直接網路路徑中檔案配接器接收位置。 <br /><br /> 如需此屬性的限制，請參閱 [限制設定 File 配接器時](../core/restrictions-when-configuring-the-file-adapter.md)。 <br/><br/>**注意︰**  的 URI，傳送埠或接收位置不能超過 256 個字元。|  
    |**檔案遮罩**|必要。 指定檔案的遮罩。 此遮罩可包含標準萬用字元值"\*"。<br /><br /> **預設值︰** \*.xml<br /><br /> **類型︰** 字串<br /><br /> 如需此屬性的限制，請參閱 [限制設定 File 配接器時](../core/restrictions-when-configuring-the-file-adapter.md)。|  
    |**公用位址**|指定此位置的公用位址。 BizTalk Server 會對外部夥伴公開此位址。<br /><br /> 若未指定此屬性，執行階段引擎會以下列位址取代：<br /><br /> file://\<*接收資料夾*\>/\<*檔案遮罩*\><br /><br /> 此屬性值必須有配接器前置詞。<br /><br /> **類型︰** 字串<br /><br /> **最小長度︰** 0<br /><br /> **最大長度︰** 256|  
    |**重試計數**|指定當網路共用上的接收位置暫時無法使用時，嘗試存取該接收位置的次數。<br /><br /> **預設值︰** 5<br /><br /> **類型︰** 長<br /><br /> **最小值︰** 0<br /><br /> **最大值︰** MAX_LONG|  
    |**重試間隔 （分鐘）**|指定當網路共用上的接收位置暫時無法使用時，嘗試存取該接收位置的重試間隔時間 (以分為單位)。<br /><br /> **預設值︰** 5 分鐘<br /><br /> **類型︰** 長<br /><br /> **最小值︰** 0<br /><br /> **最大值︰** MAX_LONG|  
  
6.  在 **驗證** 索引標籤上，執行下列動作︰  
  
    |使用|動作|  
    |--------------|----------------|  
    |**主機沒有網路共用的存取權時，使用這些認證**| 使用網路共用或 Azure 檔案共用時，才需要。 <br /><br /> **預設值︰** False<br /><br /> **類型︰** 布林值|  
    |**使用者名稱**|如果使用網路共用，請輸入已共用的權限的使用者名稱。 <br /><br />  如果使用 Azure 檔案儲存體共用，請輸入儲存體帳戶的名稱。<br/><br/>**類型︰** 字串 <br /><br />**注意︰**  如果對應到相同的網路共用的多個接收位置會設定替代的認證，則必須使用相同的認證，所有接收位置。 若您嘗試使用一組以上的認證，Windows 不允許您從相同電腦建立多個連至共用網路伺服器的連線。|  
    |**密碼**|如果使用網路共用，請輸入具有網路共用的權限的帳戶的密碼。<br /><br />  如果使用 Azure 檔案儲存體共用，請輸入儲存體帳戶存取金鑰。這會列在 Azure 入口網站。<br /><br /> **類型︰** 字串|  
  
7.  在 **批次處理** 索引標籤上，執行下列動作︰  
  
    |使用|動作|  
    |--------------|----------------|  
    |**批次中的訊息數目**|指定以一個批次提交的訊息數量上限。<br /><br /> **預設值︰** 5<br /><br /> **類型︰** Int<br /><br /> **最小值︰** 1<br /><br /> **最大值︰** 256|  
    |**批次大小上限 （以位元組為單位）**|指定一個批次的總位元組上限。<br /><br /> **預設值︰** 102400<br /><br /> **類型︰** Int<br /><br /> **最小值︰** 1024年<br /><br /> **最大值︰** MAX_LONG|  
  
     FILE 配接器將會限制先到達任一值 (訊息數目上限或是允許位元組上限) 的批次。  
  
9. 選取 [確定] 。  
  
10. 輸入適當的值在 **接收位置屬性** 對話方塊，即可完成設定接收位置，然後按一下  **確定** 儲存設定。 如需有關資訊 **接收位置屬性** 對話方塊中，請參閱 [如何建立接收位置](../core/how-to-create-a-receive-location.md)。  

## <a name="configure-the-send-port"></a>設定傳送埠

1.  在 BizTalk Server 管理主控台中，建立新的傳送埠，或按兩下現有的傳送埠進行修改。 請參閱 [如何建立傳送埠](../core/how-to-create-a-send-port2.md)。 設定所有傳送埠選項，並指定 **檔案** 的 **類型** 選項 **傳輸** 區段 **一般**  索引標籤。  
  
2.  選取 **設定** 旁 **類型**。  
  
3.  在 **一般** 索引標籤上，執行下列動作︰  
  
    |使用|動作|  
    |--------------|----------------|  
    |**目的地位置**|必要。 輸入檔案系統、 公用共用，或要寫入輸出訊息的 Azure 檔案共用位置的路徑。 您可以輸入路徑直接在 **目的地位置**, ，也可以從檔案系統使用 **瀏覽**  按鈕。 瀏覽資料夾時 **瀏覽資料夾** 對話方塊中，您也可以建立新的資料夾，即可 **建立新資料夾**。<br /><br /> 如果使用 Azure 檔案儲存體共用，請輸入 `\\yourfilestoragename.file.core.windows.net\yourfilesharename`。<br /><br /> **類型︰** 字串 <br /><br />**注意︰**  的 URI，傳送埠或接收位置不能超過 256 個字元。|  
    |**檔案名稱**|指定 FILE 傳送處理常式寫入訊息的檔案名稱。<br /><br /> 如需此屬性的限制，包括使用巨集，在檔案名稱，請參閱 [限制設定 File 配接器時](../core/restrictions-when-configuring-the-file-adapter.md)。|  
    |**複製模式**|定義將訊息寫入檔案時使用的複製模式。 有效值為：<br /><br /> **附加。** 若檔案存在，FILE 傳送處理常式會開啟檔案，並將訊息附加到檔案結尾。 若檔案不存在，FILE 傳送處理常式會建立新檔案。<br /><br /> **覆寫**。 若檔案存在，FILE 傳送處理常式會開啟檔案，並覆寫其內容。 若檔案不存在，FILE 傳送處理常式會建立新檔案。<br /><br /> **建立新的**。 若檔案不存在，FILE 傳送處理常式會建立新檔案並寫入檔案。 若檔案已存在，FILE 傳送處理常式會報告錯誤，然後依照傳送埠的一般配接器重試邏輯來處理。 此為 FILE 傳送處理常式的預設複製模式。|  
    |**允許寫入時快取**|定義將訊息寫入檔案時是否使用檔案系統快取。<br /><br /> 有效的選項包括：<br /><br /> **False** 不使用檔案系統快取。<br /><br /> **True** 使用檔案系統快取。<br /><br /> **預設值︰** False **重要事項︰**  此屬性設定為 **True** 可提升效能的潛在資料遺失的風險，File 配接器，當電源中斷，而不是所有的資料寫入至磁碟。|  
    |**寫入時使用暫存檔案**|定義是否先將輸出檔寫入暫存檔，然後等寫入作業完成後再重新命名檔案。 如果啟用此選項，則會建立暫存檔案副檔名 **BTS-WIP**。<br /><br /> 有效選項為<br /><br /> **True** File 配接器會寫入目標資料夾時，會建立暫存檔。<br /><br /> **False** File 配接器不會建立暫存檔案寫入目標資料夾時。<br /><br /> **預設值︰** False **附註︰**  這個選項時，才可以使用 **CopyMode** 屬性設定的值為 **建立新的**|  
  
4.  在 **驗證** 索引標籤上，執行下列動作︰  
  
    |使用|動作|  
    |--------------|----------------|  
    |**主機沒有網路共用的存取權時，使用這些認證**| 使用網路共用或 Azure 檔案共用時，才需要。 <br /><br /> **預設值︰** False<br /><br /> **類型︰** 布林值|  
    |**使用者名稱**|如果使用網路共用，請輸入已共用的權限的使用者名稱。 <br /><br />  如果使用 Azure 檔案儲存體共用，請輸入儲存體帳戶的名稱。<br /><br /> **類型︰** 字串|  
    |**密碼**|如果使用網路共用，請輸入具有網路共用的權限的帳戶的密碼。<br /><br />  如果使用 Azure 檔案儲存體共用，請輸入儲存體帳戶存取金鑰。這會列在 Azure 入口網站。<br /><br /> **類型︰** 字串|  
  
5.  選取 **確定** 以儲存設定。  

## <a name="set-the-properties-for-a-dynamic-send-port"></a>設定動態傳送埠屬性
  
 動態傳送埠不提供 BizTalk Server 管理主控台中的任何傳輸組態選項，因為這些屬性會隨著與訊息關聯的內容屬性一起提供。 這些屬性可以在自訂管線或協調流程中設定。 若要設定訊息組態屬性的協調流程中，您可以執行下列作業︰  
  
-   新增 **建構訊息** 圖形至協調流程。  
  
-   設定 **建構訊息** 圖形來建構新訊息。 (例如 Message_2)  
  
-   新增 **訊息指派** 圖形至 **建構訊息** 圖形。  
  
-   加入程式碼以 **訊息指派** 圖形來初始化您建構的訊息，並且設定適當的組態屬性的訊息。 下列程式碼會初始化所建構的 message_2 訊息 **建構訊息** 圖形，然後再將訊息的兩個組態屬性。 在此實例中，Message_1 原先是由協調流程接收：  
  
    ```  
    Message_2=Message_1;  
    Message_2(FILE.CopyMode)= 0; //0=Append  
    Message_2(FILE.AllowCacheOnWrite)= true;  
    Message_2(FILE.UseTempFileOnWrite)= true;  
    ```  
 
  
## <a name="configure-the-receive-or-send-handler"></a>設定接收埠或傳送處理常式
  
1.  在 BizTalk Server 管理主控台中，展開 **BizTalk Server 管理**, ，依序展開 **BizTalk 群組**, ，依序展開 **平台設定**, ，然後按一下  **配接器**。  
  
2.  在展開的配接器清單中，按一下  **檔案**, 、 在右窗格中，以滑鼠右鍵按一下接收或傳送您想要設定的處理常式。 選取 **屬性**。  
  
3.  在 **主機名稱** 清單中，選取要執行此處理常式的主控件。  
  
4.  按一下 **[確定]**。  

## <a name="more-topics-in-this-section"></a>本章節中的多個主題

[建立檔案接收位置，或以程式設計方式傳送埠](../core/create-the-receive-location-and-send-port-programmatically.md)

[File 配接器屬性結構描述和屬性](../core/file-adapter-property-schema-and-properties.md)

[設定 File 配接器時的限制](../core/restrictions-when-configuring-the-file-adapter.md)

## <a name="see-also"></a>另請參閱

 [接收和傳送伺服器的連接埠](../core/ports-for-the-receive-and-send-servers.md)   
 [最小安全性使用者權限](../core/minimum-security-user-rights.md)