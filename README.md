import java.util.*;

public class SpamEmailDetector {

    // A list of common spam keywords
    private static final List<String> SPAM_KEYWORDS = Arrays.asList(
        "win", "winner", "free", "prize", "cash", "urgent", "lottery",
        "claim", "money", "offer", "click", "buy now", "cheap", "guarantee"
    );

    public static boolean isSpam(String emailContent) {
        String content = emailContent.toLowerCase();
        int spamScore = 0;

        for (String keyword : SPAM_KEYWORDS) {
            if (content.contains(keyword)) {
                spamScore++;
            }
        }

        // You can adjust the threshold as needed
        return spamScore >= 3;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter email content:");
        String emailContent = scanner.useDelimiter("\\A").next();  // Reads entire input

        boolean spam = isSpam(emailContent);

        if (spam) {
            System.out.println("\n⚠️ This email is likely SPAM.");
        } else {
            System.out.println("\n✅ This email looks clean.");
        }

        scanner.close();
    }
}

