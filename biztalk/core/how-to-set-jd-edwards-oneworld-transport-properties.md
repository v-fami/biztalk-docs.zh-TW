---
redirect_url: /biztalk/core/adding-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 5290f424bbeb5cf54e78c903c50a6c2d945bc8cc
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-set-jd-edwards-oneworld-transport-properties"></a>如何設定 JD Edwards OneWorld 傳輸屬性

## <a name="overview"></a>概觀
「JD Edwards OneWorld 傳輸屬性系統定義」用於設計和執行階段登入。 您要設定這些認證以在設計階段瀏覽 JD Edwards OneWorld 商務功能，並在執行階段進行呼叫。  
  
 當與 JD Edwards OneWorld 建立連線時，參數會傳送到連線物件 (使用者、密碼、環境)。 它會傳回一個 JD Edwards OneWorld 應用程式商務函數。 企業/應用程式伺服器名稱與服務接聽的已定義 TCP/IP 連接埠會進一步定義認證。  
  
 從名為 jdeinterop.ini 的檔案讀取企業伺服器名稱和連接埠。 這些值必須是相同的系統定義的設定中。  
  
> [!NOTE]
>  所有項目均區分大小寫。  
  
## <a name="set-the-transport-properties"></a>設定傳輸屬性  
 在**傳輸屬性**對話方塊中，設定伺服器系統和您嘗試存取的物件特有的連接和認證參數。  
  
1.  提供認證。  
  
     您可以使用下列其中一種方法來存取 JD Edwards OneWorld 系統：  
  
    -   登入認證 （密碼、 使用者名稱）： 如果您使用此方法時，請移至步驟 5。  
  
    -   單一登入。  
  
2.  若要使用單一登入 (SSO)，選取**是**中**使用 SSO**。  
  
     如需如何設定 SSO 的詳細資訊，請參閱[配接器中的安全性](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)  
  
3.  在清單中選取分支機構應用程式。  
  
     企業單一登入工具建立的分支機構應用程式代表一個應用程式 (例如 JD Edwards OneWorld)。 Microsoft BizTalk Adapter for JD Edwards OneWorld 會使用應用程式使用者的認證。 這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 認證資料庫中擷取所得。 這些認證就是啟動 BizTalk Server 專案之應用程式使用者的認證。  
  
     如需詳細資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications3.md)。  
  
4.  展開**JD Edwards OneWorld 系統**節點，然後輸入連線的所有必要的資訊至 JD Edwards OneWorld 伺服器。  
  
     ![](../core/media/jdedadapter-02-jdesystem.gif "JDEdAdapter_02_JDESystem")  
  
     在設定連線參數後，您可以瀏覽 JD Edwards OneWorld 系統。 如需詳細資訊，請參閱[匯入 JD Edwards OneWorld 結構描述至 BizTalk Server 專案](../core/importing-jd-edwards-oneworld-schemas-into-biztalk-server-projects.md)。  
  
5.  輸入值，在代表的呼叫，例如 200，**同時呼叫數目上限**如有必要。  
  
     `Max Concurrent Calls`參數可讓您最佳化組態。 在輸送量超過後端處理能力時，可以使用這個參數來啟動訊息多載保護。 預設值為 -1，表示呼叫沒有上限。  
  
     當 BizTalk Server 將訊息提交到傳輸配接器時，會先收到來自配接器的批次。 它會在批次上叫用 `TransmitMessage` 以傳輸每個訊息。 完成傳輸時，BizTalk Server 會在批次上叫用 `Done`，這時配接器就會開始將訊息傳輸至後端。 如果 BizTalk Server 在叫用 `Done` 之前取得多個批次，可能永遠不會叫用。 藉由設定批次中的訊息數目上限，您便可以控制送到後端的訊息。  
  
     此參數的變更會在 1 分鐘內生效；BizTalk Server 必須擷取儲存在 SQL 資料庫中的配接器組態變更。  
  
6.  選取**是**如**重新整理代理程式**強制 runtimeagent.exe 和 browsingagent.exe 程序在必要時自動重新啟動。  
  
     例如，您希望處理程序在與伺服器中斷連線時自動重新啟動，或是您在伺服器加上其他項目，但是該項目並未出現在 Microsoft 配接器精靈的選項中。  
  
    > [!NOTE]
    >  這個 browsingagent.exe 要等到您結束目前的瀏覽工作階段才會重新整理。 例如，您必須先結束**新增產生的項目**瀏覽工作階段，並重新進入，才能更新 browsingagent.exe。  
  
7.  提供之後所有必要的資訊，請按一下**套用**，然後按一下 **確定**以採用連線資訊。  
  
     您必須為 BizTalk Adapter for JD Edwards OneWorld 設定連線參數，才能存取 JD Edwards OneWorld。  
  
## <a name="adapter-required-properties"></a>配接器必要屬性  
 如果沒有在 [控制台] 中設定全域環境變數，您可以在此區段中設定。  
  
|參數|Description|  
|---------------|-----------------|  
|`Host`|輸入主控件伺服器電腦名稱的名稱 (例如， `actsvr1`); 或電腦的 IP 位址 (例如， `123.456.0.789`)。|  
|JAVA_HOME|輸入 JDK 安裝的完整路徑。|  
|JDE Edwards 環境|在 JD Edwards OneWorld 中，輸入環境的名稱，例如`DV7333`。<br /><br /> DV7333 是開發環境的一般名稱，PY7333 常見於原型環境，PD7333 常見於實際執行環境。|  
|JDEdwards JAR 檔案|輸入每個 JAR 檔案的完整路徑與檔案名稱：<br /><br /> -Connector.jar<br />-Kernel.jar<br />-JDEJAccess.jar<br />-JDEActionalInterop.jar<br /><br /> 每個 JAR 檔案都必須以分號 (;) 分隔，且不得包含空格。 例如：<br /><br /> `<drive>\Connector.jar;<drive>\Kernel.jar;`|  
|密碼|輸入指定使用者的密碼。|  
|通訊埠|輸入會交換資料的連接埠號碼 (例如， `6009`)。|  
|使用者名稱|輸入將用來登入 JD Edwards OneWorld 系統的 JD Edwards OneWorld 使用者名稱。|  
  
